<template>
    <div>
        <h3>Element表单</h3>
        <hr>
        
        <el-form :model="formData" ref="elForm" :rules="formRules" label-width="80px">
            <el-form-item label="用户名" prop="username">
                <el-input v-model="formData.username"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input type="password" v-model="formData.password"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="onSubmit('elForm')">登录</el-button>
            </el-form-item>
        </el-form>

        <h3>Wan表单</h3>
        <hr>

        <wan-form :model="formData" :rules="formRules">
            <wan-form-item label="用户名" prop="username">
                <wan-input v-model="formData.username"></wan-input>
            </wan-form-item>
            <wan-form-item label="密码" prop="password">
                <wan-input type="password" v-model="formData.password"></wan-input>
            </wan-form-item>
        </wan-form>

        
    </div>
</template>
<script>
import WanForm from './WanForm.vue'
import WanFormItem from './WanFormItem.vue'
import WanInput from './WanInput.vue'
export default {
    data() {
        return {
            formData: {
                username: '',
                password: ''
            },
            formRules: {
                username: [
                    { required: true, message: '请输入用户名', trigger: 'blur'},
                    { min: 3, max: 8, message: '长度在3-8个字符', trigger: 'input'}
                ],
                password: [
                    { required: true, message: '请输入密码', trigger: 'blur'},
                    { min: 6, max: 16, message: '长度在6-16个字符', trigger: 'input'}
                ]
            }
        }
    },
    components: {
        WanForm,
        WanFormItem,
        WanInput
    },
    methods: {
        onSubmit(form) {
            this.$refs[form].validate(valid => {
                if (valid) {
                    alert('提交登录')
                } else {
                    alert('校验失败')
                }
            })
        }
    }
}
</script>