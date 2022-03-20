<template>
    <div @click="hideModal" class="dialog" v-if="show">
        <div @click.stop class="dialog__content">
            <form @submit.prevent="submitHendler">
                <input v-model="username" placeholder="username" type="text" />
                <input v-model="password" placeholder="password" type="password" />
                <button type="submit">send</button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: "ModalComponent",
    props: {
        show: {
            type: Boolean,
            default: false,
        }
    },
    data() {
        return {
            username: '',
            password: '',
        }
    },
    methods: {
        hideModal() {
            this.$emit('update:show', false)
        },
        submitHendler() {
            if (this.username && this.password) {
                fetch('/login/', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json;charset=utf-8'
                    },
                    body: JSON.stringify({ username: this.username, password: this.password })
                })
                this.username = ""
                this.password = ""
                this.hideModal()
            }

        }
    },
}
</script>

<style scoped>
.dialog {
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.5);
    position: fixed;
    display: flex;
}
.dialog__content {
    margin: auto;
    background-color: rgb(43, 42, 53);
    width: 300px;
    height: 300px;
    display: flex;
    flex-direction: column;
    text-align: center;
}
input {
    background-color: rgb(105, 118, 145);
    color: white;
    width: 260px;
    margin: 20px;
    height: 50px;
    padding-left: 10px;
}
input::placeholder {
    color: rgba(255, 255, 255, 0.5);
    text-transform: uppercase;
}
button {
    color: black;
    text-transform: uppercase;
    font-weight: 600;
    background-color: rgb(209, 209, 3);
    width: 150px;
    height: 50px;
}
</style>