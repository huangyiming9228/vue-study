<template>
    <transition name="modal-fade">
        <div class="modal-backdrop" @click="closeModal">
            <div class="modal" @click.stop>
                <div class="modal-header">
                    <slot name="header">
                        <h2>Modal弹框的标题</h2>
                        <button type="button" class="btn-close" @click="closeModal">X</button>
                    </slot>
                </div>
                <div class="modal-body">
                    <slot name="body">
                        Modal弹框主体
                    </slot>
                </div>
                <div class="modal-footer">
                    <slot name="footer">
                        Modal弹框底部
                        <button type="button" class="btn-green" @click="closeModal">关闭</button>
                    </slot>
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    name: 'Modal',
    methods: {
        closeModal() {
            this.$emit('close-modal');
        }
    }
}
</script>

<style>
.modal-backdrop { 
    position: fixed; 
    top: 0; 
    right: 0; 
    bottom: 0; 
    left: 0; 
    background-color: rgba(0,0,0,.3); 
    display: flex; 
    justify-content: center; 
    align-items: center; 
} 
.modal { 
    background-color: #fff; 
    box-shadow: 2px 2px 20px 1px; 
    overflow-x:auto; display: flex; 
    flex-direction: column; 
} 
.modal-header, 
.modal-footer { 
    padding: 15px; 
    display: flex; 
} 
.modal-header { 
    border-bottom: 1px solid #eee; 
    color: #4aae9b; 
    justify-content: space-between; 
} 
.modal-footer { 
    border-top: 1px solid #eee; 
    justify-content: flex-end; 
} 
.modal-body { 
    position: relative; 
    padding: 20px 10px; 
} 
.btn-close { 
    border: none 0; 
    font-size: 20px; 
    padding: 20px; 
    cursor: pointer; 
    font-weight: bold; 
    color: #4aae9b; 
    background-color: transparent; 
} 
.btn-green { 
    color: #fff; 
    background-color: #4aae9b;
    border: 1px solid #4aae9b; 
    border-radius: 2px; 
}

.modal-fade-enter,
.modal-fade-leave-to {
    transform: translateY(-200px);
    opacity: 0;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
    transition: all .5s;
}

</style>


