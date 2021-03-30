<template>
    <div class="send">
        <!-- <input @keydown.enter="sendEvents(inputContent)" type="text"  v-model="inputContent">
              这是原本传过来的函数可用直接放在这个函数表达式内使用。
        <button @click="sendEvents(inputContent)">发送</button> -->

         <textarea @keydown.enter="send" type="text"  v-model="inputContent"></textarea>

            <!-- <button @click="send">发送</button> -->
    </div>
</template>

<script>
export default {
    //这是是父组件chatcom传过来的方法，
    props:['sendEvents'],
    data() {
        return {
            inputContent:''
        }
    },

    methods: {
        send(){
            this.sendEvents(this.inputContent);
            this.inputContent = '';
        }
    },
}
</script>

<style lang="less" scoped>
    .send{
        width: 100%;
        height: 20%;
       
        background-color: aquamarine;
        textarea{
            width: 99%;
            height: 95%;
            resize: none;
            border: 1px  solid #cccccc;
        }
       
    }
    
</style>