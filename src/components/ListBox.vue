<template>
    <ul id="list-box">
        <li v-for="(item,key) in renderTodo"  :key="key" @click='$emit("changeStatus",item.id)'>
            <Logo :status='item.status'></Logo>
            <span>{{item.thing.length > 20 ? item.thing.slice(0,21)+'...' : item.thing}}</span>
        </li>
    </ul>
</template>
<script>
import Logo from './Flag'
export default {
    name:'list-box',
    props:['todo','typeStatus'],
    components:{
        Logo
    },
    computed:{
        renderTodo:function(){
            let newTodo = [];
            if(this.typeStatus =='all'){
                newTodo = this.todo;
            }
            else{
                let status = this.typeStatus == 'unfinished' ? false : true ;
                this.todo.forEach(function(value){
                    if(value.status == status)
                        newTodo.push(value);
                });
            }
            return newTodo;
        }
    }
}
</script>
<style>
    ::-webkit-scrollbar{
        width:0;
    }
    #list-box{
        height:80vh;
        display: flex;
        flex-direction: column;
        overflow:auto;
    }
    #list-box li{
        display: flex;
        flex-direction: row;
        box-sizing: border-box;
        height:10vh;
        line-height:10vh;
        align-items: center;
        cursor: pointer;
    }
    #list-box li img{
        width:10%;
        padding-left:5%;
        padding-right:5%;
    }
</style>