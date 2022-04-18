<template>
  <h1>{{ title }}</h1>
  <div v-if="showModal">
    <Modal :header="header" :text="text" :theme="text" @close="toggleModal" />
  </div>
  <input type="text" ref="name">
  <button @click.shift="handleClick">shift + click me</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My First App :)',
      header: 'This header from props',
      text: 'custom text',
      showModal: false
    }
  },
  methods: {
    handleClick() {
      this.text = this.$refs.name.value
      this.toggleModal()
    },
    toggleModal() {
      this.showModal = !this.showModal
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
