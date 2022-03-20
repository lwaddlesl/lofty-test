<template>
  <div>
    <ModalComponent v-model:show="modalActive" />
    <header class="header">
      <button class="sign-up" @click="signUp">sign up</button>
    </header>
  </div>
</template>

<script>
import ModalComponent from './ModalComponent.vue'

export default {
  name: "HeaderComponent",
  data() {
    return {
      modalActive: false
    }
  },
  methods: {
    signUp() {
      this.modalActive = true
    }
  },
  components: { ModalComponent }
}
</script>

<style scoped>
.header {
  height: 60px;
  width: 100%;
  background-color: rgb(105, 118, 145);
  text-align: end;
}
.sign-up {
  background-color: gray;
  width: 100px;
  height: 40px;
  margin-right: 50px;
  margin-top: 10px;
  border: none;
  color: white;
  font-weight: 600;
  font-size: large;
  font-family: monospace;
  text-transform: uppercase;
}
</style>
