// 显示表单项名称
// 提供表单容器
// 验证表单项，显示验证结果
<template>
    <div>
        <label v-if="label">{{ label }}</label>
        <slot></slot>
        <p v-if="errorMsg" style="color: red">{{ errorMsg }}</p>
    </div>
</template>

<script>
import Schema from 'async-validator';

export default {
    props: {
        label: {
            type: String,
            default: ''
        },
        prop: {
            type: String,
            default: ''
        }
    },
    provide() {
        return {
            'prop': this.prop
        }
    },
    inject: ['form'],
    data() {
        return {
            errorMsg: ''
        }
    },
    mounted() {
        this.$on('validate', this.validate)
    },
    methods: {
        validate() {
            const prop = this.prop;
            const value = this.form.model[prop];
            const rules = this.form.rules[prop];  
            
            // 创建校验器
            const schema = new Schema({
                [prop]: rules
            });

            // 校验
            schema.validate({ [prop]: value }, errors => {
                if (errors) {
                    this.errorMsg = errors[0].message;
                } else {
                    this.errorMsg = ''
                }
            })
        }
    }
 }
</script>