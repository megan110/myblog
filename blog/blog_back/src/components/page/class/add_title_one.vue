<template>
    <div class="title_one">
        <label for="">
            <b>标题:</b><el-input v-model="input" placeholder="请输入内容" style="width:400px;height:40px;margin-top:20px;"></el-input>
        
        </label>
        <label for="">
            <b>一级分类:</b>
             <el-select v-model="value" placeholder="请选择" style="width:400px;height:40px;margin-top:15px;">
                <el-option
                v-for="item in options"
                :key="item.value"
                :label="item.label"
                :value="item.value">
                </el-option>
            </el-select>
        </label>
        <label for="">
            <b>二级分类:</b>
             <el-select v-model="value" placeholder="请选择" style="width:400px;height:40px;margin-top:15px;">
                <el-option
                v-for="item in options"
                :key="item.value"
                :label="item.label"
                :value="item.value">
                </el-option>
            </el-select>
        </label>
        <label for="">
            <b>作者:</b><el-input v-model="input" placeholder="请输入内容" style="width:400px;height:40px;margin-top:20px;"></el-input>
        
        </label>
       <label for="">
            <b>推荐:</b>
            <el-radio class="radio" v-model="radio" label="1" style="width:60px;height:40px;margin-top:25px;">是</el-radio>
            <el-radio class="radio" v-model="radio" label="2" style="width:60px;height:40px;margin-top:25px;">否</el-radio>
        </label>
        <label for="">
            <b>状态:</b>
            <el-radio class="radio" v-model="radio" label="1" style="width:60px;height:40px;margin-top:25px;">显示</el-radio>
            <el-radio class="radio" v-model="radio" label="2" style="width:60px;height:40px;margin-top:25px;">隐藏</el-radio>
        </label>
        <label for="">
            <b>时间:</b>
             <el-time-picker
                v-model="value2"
                :picker-options="{
                selectableRange: '18:30:00 - 20:30:00'
                }"
                placeholder="任意时间点" style="height:40px;margin-top:20px;">
            </el-time-picker>
        </label>
        <label for="">
            <b>导读:</b>
             <textarea style="width:200px;height:100px;margin-top:20px;"></textarea>
        </label>
         <label for="">
             <input type="button" value="提交" style="width:80px;height:35px;margin-left:200px;margin-top:30px;">
         </label>
    </div>

</template>

<script>
    export default {
        data() {
            return {
                options: [{
                value: '选项1',
                label: '黄金糕'
                }, {
                value: '选项2',
                label: '双皮奶'
                },],
                value: '',
                 radio: '1',
                  value2: new Date(2016, 9, 10, 18, 40)
            }
        },
        methods: {
           
        }
    }
</script>

<style scoped>
   *{
        margin: 0;
        padding: 0;
        font-family: "微软雅黑"
    }
    .title_one{
         color: #000;
         display: flex;
         flex-direction: column;
    }
    .title_one label{
        width: 100%;
        display: flex;
        
    }
     .title_one b{
        width: 15%;
        line-height:40px;
        width: 10%;
        text-align: left;
        margin:15px 20px 0 60px;
        font-weight: normal;

    }
   
</style>