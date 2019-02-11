<template>
    <section>
        <transition-group name="list" tag="ul">                                                        <!-- <transition-group></transition-group>태그는 목록에 애니메이션을 추가할 때 사용되는 태그 tag 속성에 애니메이션이 들어갈 HTML 태그 이름(p,ul,section 등등)을 지정하면 됩니다. -->
            <li v-for= "(todoItem,index) in propsdata" :key="todoItem" class="shadow">                  <!-- 선택한 할 일을 뷰에서 인식하도록 반복 작업의 key값을 선언해야한다. -->
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                {{todoItem}}
                <span class="removeBtn" type="button" @click= "removeTodo(todoItem,index)">              <!-- @click은 v-on:click과 동일하게 동작한다.-->
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </transition-group>
    </section>
</template>
<script>
export default{
    props: ["propsdata"],
    methods:{
        removeTodo(todoItem, index){
            this.$emit("removeTodo",todoItem,index);
    }
    }
}
</script>
<style scoped>             /* 해당 .vue 컴포넌트에서만 스타일이 적용되도록 함*/
.list-enter-active, .list-laeve-active{
    transition: all 1s;
}
.list-enter, .list-leave-to{
    opacity: 0;
    transform: translateY(30px);
}
section{
    margin: 10px auto;
}
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