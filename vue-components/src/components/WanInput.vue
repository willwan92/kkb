// 显示父节点传入的数据；
// 接受表单输入，在用户输入时通知父节点
<template>
    <div>
        <input type="text" :value="value" @input="onInput">
    </div>
</template>

<script>
export default {
    props: {
        value: {
            type: String,
            default: ''
        }
    },
    data() {
        return {

        }
    },
    methods: {
        onInput(e) {
            this.$emit('input', e.target.value)
        }
    }
}
</script>