<template>
    <section>
        <ul>
            <li v-for= "(todoItem,index) in todoItems" :key="todoItem" class="shadow">                  <!-- 선택한 할 일을 뷰에서 인식하도록 반복 작업의 key값을 선언해야한다. -->
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                {{todoItem}}
                <span class="removeBtn" type="button" @click= "removeTodo(todoItem,index)">              <!-- @click은 v-on:click과 동일하게 동작한다.-->
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>
<script>
export default{
    data(){
        return{
            todoItems: []
        }
    },
    created(){
        if(localStorage.length>0){
            for(var i=0; i<localStorage.length; i++){
                this.todoItems.push(localStorage.key(i))
            }
        }
    },
    methods:{
        removeTodo(todoItem, index){
            localStorage.removeItem(todoItem);                                      // removeItem은 로컬 스토리지에서 데이터를 삭제하는 API입니다
            this.todoItems.splice(index, 1);                                        // splice()는 자바스크립트에 기본적으로 내장되어 있는 API
        }                                                                           // 배열의 특정 인덱스에서 부여한 숫자만큼의 인덱스를 삭제합니다. 일반적으로 자바스크립트 배열 프로그래밍에서 자주 사용하는 API
    }
}
</script>
<style scoped>             /* 해당 .vue 컴포넌트에서만 스타일이 적용되도록 함*/
ul{
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0px;
    text-align:left;
}

li{
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius:5px;
}

.checkBtn{
    line-height: 45px;
    color:#62acde;
    margin-right: 5px;
}

.removeBtn{
    margin-left: auto;
    color: #de4343;
}

</style>