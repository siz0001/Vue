<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do!" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>
<script>
export default{
    data(){
        return{
            newTodoItem: ''
        }
    },
    methods:{
        addTodo(){
            if(this.newTodoItem !==""){
                var value = this.newTodoItem && this.newTodoItem.trim();       // 이 문법은 왜 포함되어 있는 것일까?
                localStorage.setItem(value, value);                            // 로컬 스토리지에 데이터를 추가하는 API입니다. API 형식은 키, 값 형태이며
                this.clearInput();                                             // 저장 기능을 최대한 단순하게 하기 위해 키, 값 모두 입력 받은 텍스트로 지정합니다.
            }
        },
        clearInput(){
            this.newTodoItem="";
        }
        
    }


}
</script>
<style scoped>

input:focus{
    outline: none;
}
.inputBox{
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
}

.inputBox input{
    border-style:  none;
    font-size: 0.9rem;
}

.addContainer{
    float: right;
    background: linear-gradient(to right, #6478Fb, #8763Fb);
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
}

.addBtn{
    color: white;
    vertical-align: middle;
}


</style>