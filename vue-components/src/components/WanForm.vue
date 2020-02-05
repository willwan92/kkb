// 提供表单容器；
// 提供表单数据模型和验证规则
<template>
    <form>
        <slot></slot>
    </form>
</template>

<script>
export default {
    // provide 选项应该是一个对象或返回一个对象的函数。
    // 该对象包含可注入其子孙的属性。
    provide() {
        return {
            form: this
        }
    },
    props: {
        model: {
            type: Object,
            required: true
        },
        rules: {
            type: Object,
            default: null
        }
    }
}
</script>