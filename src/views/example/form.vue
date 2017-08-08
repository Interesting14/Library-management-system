<template>
<div v-cloak>
    <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
      <el-form-item label="书名" prop="name">
            <el-col :span="11" >
                <el-input v-model="ruleForm.name"></el-input>
            </el-col>
      </el-form-item>

      <el-form-item label="编号" prop="id">
            <el-col :span="11" >
                <el-input v-model="ruleForm.id"></el-input>
            </el-col>
      </el-form-item>

      <el-form-item label="作者" prop="author">
            <el-col :span="11" >
                <el-input v-model="ruleForm.author"></el-input>
            </el-col>
      </el-form-item>

      <el-form-item label="类别" prop="region">
            <el-col :span="11">
                <el-select v-model="ruleForm.region" placeholder="请选择书籍类别" style="width: 30%;">
                  <el-option label="教育教学" value="edu"></el-option>
                  <el-option label="青春文学" value="youth"></el-option>
                  <el-option label="科技生活" value="tech"></el-option>
                  <el-option label="人文历史" value="human"></el-option>
                  <el-option label="少儿读物" value="child"></el-option>
                </el-select>
             </el-col>
      </el-form-item>

      <el-form-item label="出版日期" required>
        <el-col :span="5" >
          <el-form-item prop="date1" >
            <el-date-picker type="date" placeholder="选择日期" v-model="ruleForm.date1" style="width: 100%;"></el-date-picker>
          </el-form-item>
        </el-col>
      </el-form-item>

      <el-form-item label="推荐书目" prop="delivery">
        <el-switch on-text="" off-text="" v-model="ruleForm.delivery"></el-switch>
      </el-form-item>

      <el-form-item label="特殊要求" prop="type">
        <el-checkbox-group v-model="ruleForm.type">
          <el-checkbox label="checkbox1" name="type">不可外借</el-checkbox>
          <el-checkbox label="checkbox2" name="type">外借押金</el-checkbox>
          <el-checkbox label="checkbox3" name="type">高级会员专属</el-checkbox>
          <el-checkbox label="checkbox4" name="type">珍藏版本</el-checkbox>
        </el-checkbox-group>
      </el-form-item>

      <el-form-item label="内容简介" prop="desc1">
            <el-col :span="11" >
                <el-input type="textarea" v-model="ruleForm.desc1"></el-input>
            </el-col>      
      </el-form-item>

      <el-form-item label="作者简介" prop="desc2">
            <el-col :span="11" >
                <el-input type="textarea" v-model="ruleForm.desc2"></el-input>
            </el-col>      
      </el-form-item>

      <el-form-item>
        <el-button type="primary" @click="submitForm('ruleForm')">立即创建</el-button>
        <el-button @click="resetForm('ruleForm')">重置</el-button>
      </el-form-item>

    </el-form>
</div>
</template>

<script>
    import { Message } from 'element-ui';
    import {global} from 'src/global/global';
    import {api} from 'src/global/api';

    export default {
        data() {
          return {
            ruleForm: {
              name: '',
              id: '',
              author:'',
              region: '',
              date1: '',
              date2: '',
              delivery: false,
              type: [],
              desc1: '',
              desc2: ''
            },
            rules: {
              name: [
                { required: true, message: '请输入书籍名称', trigger: 'blur' }
                // { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
              ],
              id: [
                { required: true, message: '请输入书籍编号', trigger: 'blur' }
              ],
              author: [
                { required: true, message: '请输入书籍作者', trigger: 'blur' }
              ],
              region: [
                { required: true, message: '请选择书籍类别', trigger: 'change' }
              ],
              date1: [
                { type: 'date', required: true, message: '请选择日期', trigger: 'blur' }
              ],
              desc1: [
                { required: true, message: '请填写内容简介', trigger: 'blur' }
              ],
              desc2: [
                { required: true, message: '请填写作者简介', trigger: 'blur' }
              ]
            }
          };
        },
        mounted() {
            var vm = this;

            vm.getFormData();



        },
        methods: {
            //根据id查询表单数据
            getFormData:function(){
                var vm = this;
                var data = this.$route.query;
                console.log('获取到url参数：',data);
                //根据url中的参数，进行ajax获取表单数据
                global.get( api.getForm,{params:{'id':data.id}}, function(res){
                      console.log('-------根据id获取表单信息：',JSON.stringify(res) )
                      if(res.body.resultCode == 0){
                           var res = res.body.data;
                                console.log('=====',res);

                                vm.ruleForm = res
                                
                      }else{
                            //alert(res.body.resultMsg)
                            Message({
                                showClose: true,
                                message: res.body.resultMsg,
                                type: 'error'
                            });
                      }

                      
                },function(res){
                    //失败回调
                },false)
            },
          submitForm(formName) {
            this.$refs[formName].validate((valid) => {
              if (valid) {
                    alert('已提交书籍信息，提交参数请看控制台');
                    console.log('提交入参：',this.ruleForm);

                    //正式编程以下代码请放到接口成功回调函数中
                    Message({
                        showClose: true,
                        message: '提交成功，正在跳转页面……',
                        type: 'success'
                    })
                    setTimeout(()=>{
                        //this.$router.push('/');
                        this.$router.go(-1)
                    },2000)
              } else {
                console.log('error submit!!');
                return false;
              }
            });
          },
          resetForm(formName) {
            this.$refs[formName].resetFields();
          }
        }
      }
</script>

<style scoped>
[v-cloak] {
  display: none;
}
.component-item{
  margin-top: 100px;
}
.code-part{
  margin-top: 20px;
}
</style>
