// 显示父节点传入的数据；
// 接受表单输入，在用户输入时通知父组件
<template>
    <div>
        <input ref="input" :type="type" :value="value" @input="onInput">
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
    mounted() {
        // 获取对应的验证规则
        const rules = this.form.rules[this.prop];
        // 绑定验证规则的事件，然后通知父节点执行验证
        rules.forEach(rule => this.bindEvent(rule.trigger))
    },
    methods: {
        bindEvent(event) {
            this.$refs['input'].addEventListener(event, () => {
                this.$parent.$emit('validate');
            })
        },
        onInput(e) {
            // 在使用该组件时，可以通过v-model实现双向数据事件绑定
            // v-model本质上是语法糖。它负责监听用户的输入事件以更新数据
            // 所以这里需要监听input的输入事件，然后触发组件的input事件
            this.$emit('input', e.target.value);
        },
    }
}
</script>