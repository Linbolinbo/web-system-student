<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <tr>
      <!-- <th scope="row">1</th> -->
      <td v-show="is_edit">{{ student.number }}</td>
      <td v-show="is_edit">{{ student.name }}</td>
      <td v-show="is_edit">{{ student.age }}</td>
      <td v-show="is_edit">{{ student.chi }}</td>
      <td v-show="is_edit">{{ student.math }}</td>
      <td v-show="is_edit">{{ student.eng}}</td>
      
      <td v-show="is_edit">
        <el-button type="text" @click="modify">修改</el-button>
       
      </td>
      <td v-show="is_edit">
        
        <el-button type="text" @click="deleteStudent">删除</el-button>
      </td>
      
      <td v-show="!is_edit"><input class="w-50" type="text" v-model="student2.number"/></td>
      <td v-show="!is_edit"><input class="w-50" type="text" v-model="student2.name"/></td>
      <td v-show="!is_edit"><input class="w-50" type="text" v-model.number="student2.age"/></td>
      <td v-show="!is_edit"><input  class="w-50" type="text" v-model.number="student2.chi"/></td>
      <td v-show="!is_edit"><input class="w-50" type="text" v-model.number="student2.math"/></td>
      <td v-show="!is_edit"><input  class="w-50" type="text" v-model.number="student2.eng"/></td>
      
      <td v-show="!is_edit">
        <el-button type="text" @click="save">保存</el-button>
        
      </td>
      <td v-show="!is_edit">
        
        <el-button type="text" >删除</el-button>
      </td>

    </tr>
</template>

<script>
import axios from 'axios'
export default {
  props:["student"],
  data() {
    return {
      is_edit:true,
      student2:[],
      
      
    }
  },
  methods: {
    modify(){
      this.is_edit=false
      this.student2=this.student
    }  ,
    save(){
      axios({
        url:"http://localhost:8080/update",
        method:"POST",
        data:this.student2
      })
      this.is_edit=true
    },
    deleteStudent(){
      axios({
        url:"http://localhost:8080/delete",
        method:"POST",
        data:this.student
      })
    },
   
    
  },
}
</script>

<style>

</style>