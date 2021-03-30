<template>
    <div class="list">
        <h1>用户列表</h1>

        <ul>
            <li v-for="(item ,index) in userlist" @click="chooseUser(index)" :key="index">
                <img :src="item.headerimg"  >
                <h6>{{item.username}}</h6>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
            
        }
    },
    props:['userlist'],

    methods: {
        // ~1这里的方法做一个子组件发送一个指令给父组件，父组件通过指令传值给子组件
        chooseUser:function(index){
            // ~2这里发送一个自定义chooseuser事件，然后把参数index也传递给父组件
                this.$emit('chooseuser',index)
        }
    },
}
</script>
 
<style lang="less" scoped>
//  这里加一个scoped，就是一个局部的css属性
    .list{
        width: 200px;
        height: 500px;
        background-color: aquamarine;
    }
    .list ul li{
        display: flex;
       
        height: 50px;
    }
    .list ul li img{
        width: 50px;
        height: 50px;
    }
</style>