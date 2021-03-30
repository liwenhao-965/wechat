<template>
    <div class="chatItem">
        <img :style="imgStyle" :src="chatitem.user.headerimg" alt="">
        <div>
            <!-- 这里定义一个插槽，预留聊天内容的信息 -->
            <slot></slot>
        </div>
    </div>
</template>


<script>
export default {
    //这里是从chatcom，他的父组件那里传过来的聊天内容的值。是经过v-for循环之后的值。
    props:['chatitem'],
    data() {
        return {
            imgStyle:{
                width:"60px",
                height:'60px'
            }
        }
    },
}
</script>

<style lang="less" scoped>
    .chatItem{
        display: flex;

    }
    
</style>

