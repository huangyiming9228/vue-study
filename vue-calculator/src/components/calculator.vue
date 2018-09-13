<template>
    <div class="calculator">
        <div class="result">
            <input type="text" class="input" v-model="current">
        </div>
        <button
            class="button"
            v-for="(button, index) in buttons"
            :key="index"
            @click="press"
        >{{button}}</button>
    </div>
</template>

<script>
export default {
    name: 'Calculator',
    data() {
        return {
            current: '',
            buttons: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '(', ')','+', '-', '*', '/', '<=', 'C', '=']
        };
    },
    methods: {
        press(event) {
            let vm = this;
            let key = event.target.textContent;
            if (key === 'C') {
                vm.current = '';
            } else if (key === '<=') {
                vm.current = vm.current.slice(0, vm.current.length - 1);
            } else if(key === '=') {
                vm.current = eval(vm.current);
            } else {
                vm.current += key;
            }
        }
    }
}
</script>

<style>
.calculator {
    width: 440px;
    padding: 20px;
    border-radius: 5px;
    margin: 20px auto;
    font-size: 16px;
    background-color: hsl(0, 0%, 20%);
}

.input {
    width: 420px;   
    height: 50px;
    border-radius: 0px;
    border: 1px solid hsl(0, 0%, 0%);
    background-color: #333333;
    color: #d9d9d9;
    padding: 0 5px 0 5px;
    margin: 0 0px 10px 0px;
    font-size: 30px;
}

.input:focus,
.input:active {
    border-color: #03a9f4;
    box-shadow: 0 0 4px #03A9F4;
    outline: none 0;
}

.button {
    margin: 3px;
    width: 63px;
    border: 1px solid hsl(0, 0%, 5%);
    height: 30px;
    border-radius: 4px;
    color: hsl(0, 0%, 85%);
    background-color: hsl(0, 0%, 10%);
    cursor: pointer;
    outline: none;
}

button:last-child {
    background-color: hsl(120, 100%, 25%);
    width: 133px;
}

button::-moz-focus-inner {
    border-color: transparent;
}
</style>
