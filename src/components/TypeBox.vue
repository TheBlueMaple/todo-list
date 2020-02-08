<template>
    <ul id='type-box'>
        <li @click='$emit("input","all")'>
            <img :src="assetsImg.all" />
            <span :class="{'font-weight':value=='all'}">全部任务</span>
        </li>
        <li @click='$emit("input","unfinished")'>
            <img :src="assetsImg.unfinished" />
            <span :class="{'font-weight':value=='unfinished'}">未完成</span>
        </li>
        <li @click='$emit("input","complete")'>
            <img :src="assetsImg.complete" />
            <span :class="{'font-weight':value=='complete'}">已完成</span>
        </li>
    </ul>
</template>
<script>
import all from '../assets/all.svg'
import unfinished from '../assets/unfinished.svg'
import complete from '../assets/complete.svg'
export default {
    name:'type-box',
    props:['value'],
    data:function(){
        return {
            assetsImg:{
                all,
                unfinished,
                complete
            }
    }
    }     
}
</script>
<style>
    #type-box{
        height:10vh;
        display: flex;
        flex-direction: row;
        background-color:rgba(56, 140, 219, 0.2);        
    }
    #type-box li{
        display: flex;
        justify-content: center;
        align-items: center;
        flex-grow: 1;
        flex-direction: column;
        padding-top:0.3em;
        padding-bottom:0.3em;
        cursor: pointer;
    }
    #type-box li img{
        width:20%;
        margin-bottom: 0.5em;
    }
    .font-weight{
        font-weight: bold;
    }
</style>