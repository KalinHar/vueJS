<template>
  <h1>{{ title }}</h1>

  <teleport to=".modals"  v-if="showModal">
    <Modal @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">more info</a>
        <p>{{ text }}</p>
      </template>
    </Modal>
  </teleport>

  <teleport to=".modals" v-if="showModal2">
    <Modal @close="toggleModal2">
      <h1>Modal 2</h1>
    </Modal>
  </teleport>

  <input type="text" ref="name">
  <button @click.shift="handleClick">shift + click me</button>
  <button @click="handleClick2">To modal 2</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My First App :)',
      text: "",
      showModal: false,
      showModal2: false,
    }
  },
  methods: {
    handleClick() {
      this.text = this.$refs.name.value
      this.toggleModal()
    },
    handleClick2() {
      this.toggleModal2()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2
    }
  }
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
