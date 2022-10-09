<template>
<!-- 登录的 haha-->
  <div>
    <div class="wrapper">
      <h1>请输入账号密码进行登录</h1>
      <div class="wrapper-login">
        <!-- 有获取焦点和失去焦点两个事件 -->
        <div>
          <input type="text" v-model="username" @focus="showUser"  @blur="closeUser"/>账号
        </div>
        <!-- 显示用户列表 -->
        <ul v-if="showClose">
          <li @click="chooseUser(user)" v-for="user in userArr" :key="user.id">
            {{ user.userName }}
          </li>
        </ul>
      </div>
      <br /><br />
      <br /><br /><br />
      <div><input type="password" v-model="password" />密码</div>
      <div>
        <input type="checkbox" v-model="checked" @input="check" />是否记住密码
      </div>
      <br />
      <button @click="submitUser">登录</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      username: "",
      password: "",
      userArr: [],
      checked: false,
      showClose: false,
    };
  },
  mounted() {
  //  创建用户列表的数组，从local storage中取得
    var len = localStorage.length; // 获取长度
    console.log(len); // 输出5

    for (var i = 0; i < len; i++) {
      // 获取key 索引从0开始
      var getKey = localStorage.key(i);
      // 获取key对应的值
      var getVal = localStorage.getItem(getKey);
      // 放进数组
      this.userArr.push({
        id: i,
        userName: getKey,
        passWord: getVal,
      });
    }
    console.log(this.userArr);
  },

  methods: {
    //单个复选框的方法确定是否存储账号密码
    check() {
      this.checked = !this.checked;
    },
    // 提交用户的方法
    submitUser() {
      if (this.checked) {
        localStorage.setItem(`${this.username}`, `${this.password}`);
        this.username = "";
        this.password = "";
        this.checked = false;
        location.reload();
      }else{
         this.username = "";
        this.password = "";
       
      }
    },
    // 显示用户列表的方法
    showUser() {
      this.showClose = true;
    },
    // 关闭用户列表的方法
    closeUser(){
      setTimeout(()=>{this.showClose = false},200)
     
    },
    // 选择用户快捷登录的方法
    chooseUser(e) {
      console.log(e);
     
      this.username = e.userName;
      this.password = e.passWord;
      // setTimeout(()=>{this.showClose = false},100)
       this.showClose = false;
    },
  },
};
</script>

<style scoped>
.wrapper{
  width:400px;
  height:500px;
  margin:0 auto;
  border:1px solid black;
}
.wrapper-login {
  
  position: relative;
}
ul {
  position: absolute;
  top: 10px;
  left:60px;

  
}
ul li {
  width:168px;
  list-style: none;

  background: lightblue;
}
ul li:hover {
  cursor: pointer;
  background:lightgray;
}
</style>
