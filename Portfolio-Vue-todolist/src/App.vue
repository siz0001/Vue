<template>                                                                      <!-- 최상위 컴포넌트 -->
    <div id="app">
      <TodoHeader></TodoHeader>
      <TodoInput></TodoInput>
      <TodoList></TodoList>
      <TodoFooter></TodoFooter>
    </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";                             // 싱글 파일 컴포넌트 체계(.vue 파일 체계)에서는 특정 컴포넌트에서 다른 위치에 있는 컴포넌트의 내용을 불러올 때 아래 형식을 사용합니다.
import TodoInput from "./components/TodoInput.vue";                               // import 불러온 파일의 내용이 담길 객체 from "불러올 파일 위치";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";
export default {
  data(){
    return{
      todoItems: []
    }
  },
  components: {
    "TodoHeader": TodoHeader,
    "TodoInput": TodoInput,
    "TodoList": TodoList,
    "TodoFooter": TodoFooter
  }
  
}
</script>

<style>
body{
    text-align: center;
    background-color: #f6f6f8;
}
input{
  border-style: groove;
  width: 200px;
}
button{
  border-style: groove;
}
.shadow{
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
