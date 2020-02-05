// 显示父节点传入的数据；
// 接受表单输入，在用户输入时通知父组件
<template>
    <div>
        <input :type="type" :value="value" @input="onInput">
    </div>
</template>

<script>
export default {
    props: {
        value: {
            type: String,
            default: ''
        },
        type: {
            type: String,
            default: 'text'
        }
    },
    inject: ['form', 'prop'],
    data() {
        return {

        }
    },
    mounted() {
        console.log(this.form.rules[this.prop])
    },
    methods: {
        onInput(e) {
            // 在使用该组件时，可以通过v-model实现双向数据事件绑定
            // v-model本质上是语法糖。它负责监听用户的输入事件以更新数据
            // 所以这里需要监听input的输入事件，然后触发组件的input事件
            this.$emit('input', e.target.value);

            // 通知父组件执行校验
            this.$parent.$emit('validate');
        }
    }
}
</script>