// 显示表单项名称
// 提供表单容器
// 验证表单项，显示验证结果
<template>
    <div>
        <label v-if="label">{{ label }}</label>
        <slot></slot>
        <p v-if="errorMsg">{{ errorMsg }}</p>
    </div>
</template>

<script>
export default {
    props: {
        label: {
            type: String,
            default: ''
        }
    },
    data() {
        return {
            errorMsg: ''
        }
    }
}
</script>