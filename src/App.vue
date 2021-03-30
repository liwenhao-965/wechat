<template>
  <div id="app">
    
    <!-- 这里需要父组件传值到子组件，数据都是在父组件里面被定义的。然后一系列子组件发射指令操作父组件，父组件传值给子组件的操作都在里面 -->
   <div class="contend">

     <!-- ~6这里就是传递过去的数据，由子组件去接受 -->
     <chat-com :cuspointuser = 'cuspointuser'></chat-com>

      <!-- ~3 这里的chooseuser的自定义修饰符指令是通过子组件发射过来的，然后触发父组件里面的方法，操作父组件里面的值 -->
      <userlist-com :userlist = "userlist" @chooseuser = 'toggleuser'></userlist-com>
   </div>

  </div>
</template>

<script>

import chatCom from './components/chatcom'
import userlistCom from './components/userlist'
export default {
     name:'app',
     components:{
       chatCom,userlistCom
     },
     data() {
       return {
         msg:'老陈聊天',
         userlist:[
           {
             username:'小明',
             headerimg:"https://dss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3717120934,3932520698&fm=26&gp=0.jpg"
           },
                      {
             username:'校长',
             headerimg:"https://dss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3717120934,3932520698&fm=26&gp=0.jpg"
           },
                      {
             username:'小黑',
             headerimg:"https://dss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3717120934,3932520698&fm=26&gp=0.jpg"
           }
         ],
         cuspointuser:
             {
              //  ~5这里是定义个当前点击的数组对象，然后返回给子组件，就是点击到哪一个，就传哪一个给子组件
             username:'小明',
             headerimg:"https://dss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3717120934,3932520698&fm=26&gp=0.jpg"
           }
         
       }
     },

     methods: {
       toggleuser:function(index){    
         this.cuspointuser = this.userlist[index];
         // ~4这个地方是通过点击事件，把子组件的index值传过来，通过遍历数组位置，操作index数值，再把响应的数值数据传递给子组件展示。
       }
     },
}
</script>


<style lang="less" scoped>
    .contend{
      display: flex;
      width: 800px;
      height: 700px;
      margin: 100px auto;
    }
  
</style>
