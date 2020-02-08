<template>
    <div id="input-box">
        <input type="text" v-bind:value='value' v-on:input = '$emit("input",$event.target.value)'  v-on:keyup.enter='$emit("submitItem")' placeholder="请键入待办事件"><button v-on:click='$emit("submitItem")'>加入</button>
    </div>
</template>
<script>
export default {
    name:'input-box',
    props:['value']
}
</script>
<style>
    #input-box{
        height:10vh;
        display: flex;
        justify-content: space-around;
        align-items: center;
    }
    #input-box input{
        line-height:3em;
        height:3em;
        width:80%;
        border-radius: 1em;
        border:1px solid blueviolet;
        outline: none;
        padding-left:1em;
        padding-right:1em;
        box-sizing: border-box;
        background-color:rgba(255, 255, 255, 0.5)
    }
    #input-box button{
        width:15%;
        background:blueviolet;
        border: none;
        border-radius: 0.5em;
        box-sizing: border-box;
        height:3em;
        cursor: pointer;
    }
</style>