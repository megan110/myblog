<template>
    <div>
        <table v-for="i in alldata">
        <tr style="background:pink">
            <td>一级类名：{{i.onedata.enname}}</td>
            <td>标识:{{i.onedata.cnname}}</td>
            <td>
                <input type="button" value="编辑" @click="handleEdit()">
                <input type="button" value="删除"  @click="handleDelete(i.onedata.id,i.onedata.enname)">
            </td>
        </tr>
         <tr v-for="j in i.twodata">
            <td>二级类名：{{j.enname}}</td>
            <td>标识:{{j.cnname}}</td>
            <td>
                <input type="button" value="编辑" @click="handleEdits()">
                <input type="button" value="删除" @click="handleDeletes(i.onedata.id,j.id,j.enname)">
            </td>
        </tr> 
    </table>
    </div>
</template>
<script>
    export default {
        data() {
            return{
                alldata:[],
                id:"",
                enname_one:"",
                oneId:"",
                twoId:"",
            }       
        },
        methods:{
             // 一级修改
            handleEdit() {
                var _this=this;
                this.axios.post("/api/back_class/amend_class_one").then(function(data){
                    console.log(data);
                    if(data.data.code=="1052"){
                        _this.alldata = data.data.data
                        _this.$message({
                            message: data.data.msg,
                            type: 'success'
                        })
                        
                    }else{
                        _this.$message({
                            message: data.data.msg,
                            type: 'error'
                        })
                    }
                    
                })
            },
                //二级修改
            handleEdits() {
                var _this=this;
                this.axios.post("/api/back_class/amend_class_two",function(data){
                     console.log(data);
                    // if(data.data.code=="1071"){
                    //     _this.alldata = data.data.data
                    //     _this.$message({
                    //         message: data.data.msg,
                    //         type: 'success'
                    //     })
                        
                    // }else{
                    //     _this.$message({
                    //         message: data.data.msg,
                    //         type: 'error'
                    //     })
                    // }
                })
            },
            //一级删除
            handleDelete(id,enname_one) {
                var _this=this;
                console.log(id)
                this.axios.post("/api/back_class/delete_one",{id:id,enname_one:enname_one}).then(function(data) {
                    console.log(data)
                    if(data.data.code=="1071"){
                        _this.alldata = data.data.data
                        _this.$message({
                            message: data.data.msg,
                            type: 'success'
                        })
                    }else{
                        _this.$message({
                            message: data.data.msg,
                            type: 'error'
                        })
                    }
                })
            },
            //二级删除
             handleDeletes(oneId,twoId,enname_one) {
                 var _this=this;
                this.axios.post("/api/back_class/delete_two",{oneId:oneId,twoId:twoId,enname_one:enname_one}).then(function(data) {
                   console.log(data)
                    if(data.data.code=="1071"){
                        _this.alldata = data.data.data
                        _this.$message({
                            message: data.data.msg,
                            type: 'success'
                        })
                    }else{
                        _this.$message({
                            message: data.data.msg,
                            type: 'error'
                        })
                    }
                })
            },
        },
        mounted(){
            var _this=this;
            this.axios.get("/api/back_class/class_list").then(function(data) {
                _this.alldata = data.data.data
                console.log(_this.alldata)
            }.bind(this))
        }
    }
</script>

<style scoped>
    *{
        color: #000;
    }
    table{
        width:800px;
        height: 40px;
        line-height: 30px;
        border-collapse: collapse;
        text-align: center;
        margin:30px 0 0 100px;
    }
    table tr{
        width:800px;
        height: 40px;
    }
    table tr td{
        width: 200px;
        border:1px solid #000;
        
    }
    input{
        width:80px;
        height: 30px;
        color: #fff;
        outline: none;
        border:none;
        line-height: 30px;
        margin-top: 2px; 
    }
    input:nth-child(1){
        background: green;
    }
    input:nth-child(2){
        background:#ccc ;
    }
</style>