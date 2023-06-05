<template>
    <tr>
        <td v-show="!is_edit">{{ student.number}}</td>
        <td v-show="!is_edit">{{ student.name}}</td>
        <td v-show="!is_edit">{{ student.age}}</td>
        <td v-show="!is_edit">{{ student.chi}}</td>
        <td v-show="!is_edit">{{ student.math}}</td>
        <td v-show="!is_edit">{{ student.eng}}</td>
        <td v-show="!is_edit">
            <!-- <el-button type="info" @click="modify">修改</el-button>
            <div><el-button type="danger" @click="deleteStudent">删除</el-button></div> -->
            <el-button type="primary" @click="modify" icon="el-icon-edit" circle ></el-button>
            <div><el-button type="danger" @click="deleteStudent" icon="el-icon-delete" circle ></el-button></div>
        </td>
        <!-- <td v-show="!is_edit">
            <el-button type="danger" @click="deleteStudent">删除</el-button>
        </td> -->
        
        <td v-show="is_edit"><input class="w-50" type="text" v-model.number="student.number"></td>
        <td v-show="is_edit"><input class="w-50" type="text" v-model="student.name"></td>
        <td v-show="is_edit"><input class="w-50" type="text" v-model.number="student.age"></td>
        <td v-show="is_edit"><input class="w-50" type="text" v-model.number="student.chi"></td>
        <td v-show="is_edit"><input class="w-50" type="text" v-model.number="student.math"></td>
        <td v-show="is_edit"><input class="w-50" type="text" v-model.number="student.eng"></td>
        <td v-show="is_edit">
            <!-- <el-button type="success" @click="save">保存</el-button>
            <div><el-button type="danger">删除</el-button></div> -->
            <el-button type="success" @click="save" icon="el-icon-check" circle ></el-button>
            <div><el-button type="danger" icon="el-icon-delete" circle ></el-button></div>
        </td>
        <!-- <td v-show="is_edit">
            <el-button type="danger">删除</el-button>
        </td> -->
    </tr>
</template>
<script>
import axios from 'axios';
export default{
    props:["student"],
    data() {
        return {
            is_edit:false
        };
    },
    methods: {
        modify(){
            this.is_edit = true;
        },
        save(){
            axios({
                url:"http://localhost:8080/update",
                method:"POST",
                data:this.student
            })
            this.is_edit=false;
        },
        deleteStudent(){
            axios({
                url:"http://localhost:8080/delete",
                method:"POST",
                data:this.student
            })
        }
    },
}
</script>