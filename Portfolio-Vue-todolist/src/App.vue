<template>                                                                      <!-- 최상위 컴포넌트 -->
    <div id="app">
      <Navbar></Navbar>
      <div id="container">                                                              <!-- 중복 데이터 발생시 오류 모달 출력하는 기능 추가하기 -->
      <TodoHeader></TodoHeader>
      <TodoInput v-on:addTodo="addTodo" @duplicateData="duplicateData" ></TodoInput>
      <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
      <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
      </div>    
    </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import TodoHeader from "./components/TodoHeader.vue";                             // 싱글 파일 컴포넌트 체계(.vue 파일 체계)에서는 특정 컴포넌트에서 다른 위치에 있는 컴포넌트의 내용을 불러올 때 아래 형식을 사용합니다.
import TodoInput from "./components/TodoInput.vue";                               // import 불러온 파일의 내용이 담길 객체 from "불러올 파일 위치";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";
export default {
  data(){
    return{
      todoItems: []                                                               // 데이터 속성 todoItems 선언
    }
  },
  created(){
        if(localStorage.length>0){
            for(var i=0; i<=localStorage.length; i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
  },
  methods:{
    addTodo(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index){
      localStorage.removeItem(todoItem);                                      // removeItem은 로컬 스토리지에서 데이터를 삭제하는 API입니다
      this.todoItems.splice(index, 1);                                        // splice()는 자바스크립트에 기본적으로 내장되어 있는 API
    },                                                                           // 배열의 특정 인덱스에서 부여한 숫자만큼의 인덱스를 삭제합니다. 일반적으로 자바스크립트 배열 프로그래밍에서 자주 사용하는 API
    clearAll(){
      localStorage.clear();
      this.todoItems=[];
    },
    duplicateData(){
      alert("이미 작성된 할 일입니다.");
    }
  },
  components: {
    "TodoHeader": TodoHeader,
    "TodoInput": TodoInput,
    "TodoList": TodoList,
    "TodoFooter": TodoFooter,
    "Navbar": Navbar
  }
}
</script>
<style>
body{
    text-align: center;
    background-color: white;
    margin:0px;
}
input{
  border-style: groove;
  width: 200px;
}
button{
  border-style: groove;
}
#container{
  padding: 10px 10px;;
}
.shadow{
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
