<template>
    <div>
        <div class="inputBox shadow" >
            <input type="text" v-model="newTodoItem" placeholder="type what you have to do"
            v-on:keyup.enter="addTodo">
            <span class="addContainer" v-on:click="addTodo">
                <i class="addBtn fas fa-plus" aria-hidden="true"></i>
            </span>
            
        </div>
    </div>
</template>
<script>
export default {
    data(){
        return{
            newTodoItem:''
        }
    },
    methods:{
        //예외 처리 코드 만들기. 만약 input에 아무것도 입력되지 않았을 경우 
        addTodo(){
            // console.log(this.newTodoItem)
            if(this.newTodoItem !== "" ){
                //문자열 앞 뒤 의 공백 제거 trim()
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo',value);
                this.clearInput();
            }
        },
        clearInput(){
            this.newTodoItem = '';
        }
    }
}
</script>
<style scoped>
    input:focus{
        outline:none;
    }
    .inputBox{
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input{
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer{
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn{
        color: white;
        vertical-align: middle;
    }
</style>