<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do!" v-on:keydown.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
        <modal v-if= "showModal" @close= "showModal = false">
            <h3 slot="header">경고</h3>
            <span slot="footer" @click= "showModal = false">
                할 일을 입력하세요.
                <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
            </span>
        </modal>
    </div>
</template>
<script>
import Modal from "./common/Modal.vue"

export default{
    data(){                                                                    // 이 부분은 무엇일까?
        return{
            newTodoItem: '',
            showModal: false
        }
    },
    methods:{
        addTodo(){
            if(this.newTodoItem !==""){
                var value = this.newTodoItem && this.newTodoItem.trim();       // 이 문법은 왜 포함되어 있는 것일까?
                this.$emit("addTodo",value);                                   // 로컬 스토리지에 데이터를 추가하는 API입니다. API 형식은 키, 값 형태이며
            }
            else if(this.newTodoItem == ""){
                this.showModal = !this.showModal;
            }
                this.clearInput();                                             // 저장 기능을 최대한 단순하게 하기 위해 키, 값 모두 입력 받은 텍스트로 지정합니다.
        },
        clearInput(){
            this.newTodoItem="";
        },
        duplicate(newTodoItem){
            
        }
        
    },
    components: {
            Modal: Modal
    }


}
</script>
<style scoped>

input:focus{
    outline: none;
}
input {
    background-color:  blueviolet;
    color: white;
    text-align: center;
    
}
input::-ms-input-placeholder { color: white; }
input::-webkit-input-placeholder { color:white; } 
input::-moz-placeholder { color:white; }                        /*placeholder 색깔 바꾸기*/
.inputBox{
    background: blueviolet;
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