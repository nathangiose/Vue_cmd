<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to=".modals" v-if="showModal">
      <Modal  theme="sale" @close="toggleModal">
        <template v-slot:links>
          <a href="#">sign up now</a>
          <a href="#">more info</a>
        </template>
        <h1>Ninja Givaway!</h1>
        <p>Grab your ninja swag for half price!</p>
      </Modal>
  </teleport>

  <teleport to=".modals" v-if="showModalTwo">
      <Modal @close="toggleModalTwo">
        <h1>Sign up to the news letter</h1>
        <p>For updates and promo codes!</p>
      </Modal>
  </teleport>

  <button @click.alt="toggleModal">Open Modal (alt)</button>
  <button @click="toggleModalTwo">Open Modal</button>
  <input type="text" ref="name">
  <button @click="handleClick">Click me</button>
</template>

<script>
import Modal from './components/Modal.vue' //importing the modal from
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'This is my Vue app :)',
      // header: 'Sign up for the Giveaway!',
      // text: "Grab your ninja swag for half price!",
      showModal: false,
      showModalTwo: false,
      

    } 
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
  // components: {
  //   HelloWorld
  // }
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

h1 {
  border-bottom: 1px solid #add;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
