<template>
    <div id="app">
        <button type="button" class="btn" @click="showModal">打开Modal</button>
        <modal v-show="isModalVisible" @close-modal="closeModal">
            <template slot="body">
                <label>姓名：<input type="text"></label>
            </template>
        </modal>
    </div>
</template>

<script>
import Modal from "./components/Modal";
export default {
    name: 'App',
    components: {
        Modal
    },
    data() {
        return {
            isModalVisible: false
        };
    },
    methods: {
        showModal() {
            this.isModalVisible = true;
        },
        closeModal() {
            this.isModalVisible = false;
        }
    }
}
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
