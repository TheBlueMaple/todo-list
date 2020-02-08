<template>
  <div id="app">
    <InputBox v-model='inputContent' @submitItem = 'submitItem'></InputBox>
    <ListBox :todo='todo' :typeStatus='typeStatus' @changeStatus='changeStatus'></ListBox>
    <TypeBox v-model='typeStatus'></TypeBox>
  </div>
</template>

<script>
import InputBox from './components/InputBox'
import ListBox from './components/ListBox'
import TypeBox from './components/TypeBox'
import Todo from './assets/todo.json'
export default {
  name: 'App',
  data:function(){
    return {
      todo:Todo,
      inputContent:'',
      typeStatus:'unfinished'
    }
  },
  components:{
    InputBox,
    ListBox,
    TypeBox
  } ,
  methods:{
    submitItem:function(){
      if(this.inputContent.trim() == '')
        return;
      this.todo.push({
        id:this.todo.length,
        thing:this.inputContent.trim(),
        status:false
      });
      this.inputContent = '';
    },
    changeStatus:function(id){
      this.todo.some((item)=>{
        if(item.id == id){
          item.status = !item.status;
          return true;
        }
      });
    }
  }
}
</script>

<style>
  *{
    margin:0;
    padding:0;
    list-style: none;
    font-family:'幼圆'
  }
  #app{
    display: flex;
    flex-direction: column;
    width:100%;
    max-width:400px;
    height:100vh;
    margin:auto;
    background-color:rgba(56, 140, 219, 0.1);
  }
</style>
