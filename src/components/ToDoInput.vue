<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
        <i class="fa-solid fa-plus addBtn"></i>
    </span>
    <Modal v-if="showModal" @close="showModal = false"> <!--showModal이 True가 되면 이 모달이 보인다-->
        <template v-slot:header>
            <h3>
                안내
                <i class="fa-solid fa-circle-xmark" @click="showModal = false"></i>
            </h3>
        </template>
        <template v-slot:body>
            <span>빈 칸은 입력할 수 없습니다</span>
        </template>
    </Modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'

export default {
    data() {
        return {
            newTodoItem:"",
            showModal: false
        }
    },
    methods:{
        addTodo() {
            if (this.newTodoItem !== '') {
                this.$emit('addTodoItem', this.newTodoItem);
                this.clearInput();
            }
            else {
                this.showModal = !this.showModal;
            }
        },  
        clearInput() {
            this.newTodoItem = '';
        }
    },
    components: {
        Modal: Modal,
    }

}
</script>

<style scoped>
    input:focus {
        outline: none;
    }

    .inputBox {
        background-color: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }

    .inputBox input {
        border-style: none;
        font-size: 0.9rem;
    }

    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478Fb, #8763FB);
        display: block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn {
        color: white;
        vertical-align: middle;
    }

    .closeModalBtn {
        color: #42b983;
    }

</style>