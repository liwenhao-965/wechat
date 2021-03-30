<template>
    <div class="chat">
        <h6>{{cuspointuser.username}}</h6>

        <div class="chatlist">
            <chatitem-com v-for="(item ,index) in chatlist" :key="index" :chatitem='item'>
                {{item.chatcontent}}
            </chatitem-com>
        </div>

        <chatinput-com :sendEvents = 'sendEvent'></chatinput-com>
    </div>
</template>

<script>

import chatinputCom from './chatinputcom'

import chatitemCom from './chatItem'
export default {
    data() {
        return {
            chatlist:[
                {
                    user:{
                        username:'小明',
                        headerimg:'https://dss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3717120934,3932520698&fm=26&gp=0.jpg'
                    },
                    chatcontent:'今天吃了吗'
                }
            ]
        }
    },
    // ~7这里是把父组件传递的属性值再传递给这个组件
    props:['cuspointuser'],
    components:{
        chatinputCom,chatitemCom
    },
    methods: {
                sendEvent(val){
               this.chatlist.push({
                        user:{
                        username:'小明',
                        headerimg:'https://dss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3717120934,3932520698&fm=26&gp=0.jpg'
                    },
                    chatcontent:val
               })
        }
    },
}
</script>

<style lang="less" scoped>
    .chat{
        width:600px ;
        height: 500px;
        border: 1px solid #cccccc;
        h6
        {
            height: 10%;
            margin: 0;
        }
        .chatlist{
            height: 70%;
        }

    }
</style>