// 提供表单容器；
// 提供表单数据模型和验证规则
<template>
    <form>
        <slot></slot>
    </form>
</template>

<script>
export default {
    props: {
        model: {
            type: Object,
            required: true
        },
        rules: {
            type: Object,
            default: Null
        }
    }
}
</script>