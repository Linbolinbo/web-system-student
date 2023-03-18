<template>
  <div id="app">
    <div class="col-8 offset-2">
      <table class="table caption-top table-hover">
      <caption class="text-center">
        <h1>学生管理系统</h1>
        <el-button type="primary" @click="getStudents">获取学生信息</el-button>
        <el-button type="warning" @click="dialogVisible = true">添加学生</el-button>
        <!-- 登录 -->
      <el-button type="text" @click="dialogVisiblein = true">登录</el-button>

<el-dialog
  title="登录"
  :visible.sync="dialogVisiblein"
  width="30%"
  :before-close="handleClosein">
  <span>用户名:</span>
  <input type="text" v-model="userLogin.username">
  <br><br>
  <span>密码:</span>
  <input type="password" v-model="userLogin.password">
  <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisiblein = false">取 消</el-button>
    <el-button type="primary" @click="login">登 录</el-button>
  </span>
</el-dialog>
<!--组册  -->
<el-button type="text" @click="dialogVisibleres = true">注册</el-button>

<el-dialog
  title="注册"
  :visible.sync="dialogVisibleres"
  width="30%"
  :before-close="handleClosein">
  <span>用户名:</span>
  <input type="text" v-model="userregister.username">
  <br><br>
  <span>密码:</span>
  <input type="password" v-model="userregister.password">
  <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisibleres = false">取 消</el-button>
    <el-button type="primary" @click="resion">注册</el-button>
  </span>
</el-dialog>



<el-dialog
  title="提示"
  :visible.sync="dialogVisible"
  width="30%"
  :before-close="handleClose">
  <span>添加学生信息</span>
  <span slot="footer" class="dialog-footer">
    <el-button @click="dialogVisible = false">取 消</el-button>
    <el-button type="primary" @click="addStudents">添加</el-button>
  </span>

  <div>学号</div><input v-model="newStudent.number"/>
  <div>姓名</div><input v-model="newStudent.name"/>
  <div>年龄</div><input v-model.number="newStudent.age"/>
  <div>语文</div><input v-model.number="newStudent.chi"/>
  <div>数学</div><input v-model.number="newStudent.math"/>
  <div>英语</div><input v-model.number="newStudent.eng"/>

</el-dialog>
      </caption>
  <thead>
    <tr>
      <th scope="col">学号</th>
      <th scope="col">姓名</th>
      <th scope="col">年龄</th>
      <th scope="col">语文</th>
      <th scope="col">数学</th>
      <th scope="col">英语</th>
      <th scope="col">操作</th>

    </tr>
  </thead>
  <tbody>
    <Student v-for="item in students" :key="item.id" :student="item"></Student>
   
  </tbody>
</table>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Student from '@/components/Student.vue'
export default {
  data() {
    return {
      userLogin:{
        username:"",
        password:""
      },
      userregister:{
        username:"",
        password:""
      },
      students:[],
      dialogVisible: false,
      dialogVisiblein: false,
      dialogVisibleres:false,
      newStudent:{
        number:"",
        name:"",
        age:"",
        chi:"",
        math:"",
        eng:"",
        
      }
    }
  },
  methods: {
    getStudents(){
      if(sessionStorage.getItem("isLogined")=="true"){
        axios({
        url:"http://localhost:8080/students",
        method:'GET'
      }).then(res=>{
        this.students=res.data
      })
      }else{
        alert("请登录成功后再进行此操作")
      }
    },
    handleClose(done) {
        this.$confirm('确认关闭？')
          .then(() => {
            done();
          })
          .catch(() => {});
      },
      addStudents(){
        if(sessionStorage.getItem("isLogined")=="true"){
          axios({
          url:'http://localhost:8080/add',
          method:'POST',
          data:this.newStudent
        })
      }else{
        alert("请登录成功后再进行此操作")
      }
        
        this.dialogVisible = false
      },
      handleClosein(done) {
        this.$confirm('确认关闭？')
          .then(() => {
            done();
          })
          .catch(() => {});
      },
      login(){
        axios({
          url:'http://localhost:8080/login',
          data:this.userLogin,
          method:'post'
        }).then(res=>{
          if(res.data=="1"){
            sessionStorage.setItem("isLogined","true")
            alert("登录成功")
          }else{
            alert("用户名或密码错误")
          }
        })
        this.dialogVisiblein=false
      },
      resion(){
        axios({
          url:'http://localhost:8080/register',
          data:this.userregister,
          method:'post'
        }).then(res=>{
          if(res.status==200){
            alert("注册成功")
          }else{
            alert("注册失败")
          }
        })
        
        this.dialogVisibleres=false

      }
  },
  components: {
    Student
  }
}
</script>

<style>

</style>
