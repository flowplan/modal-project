<template>
  <!--HTML-->
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <h1>{{ title }}</h1>

  <!-- <input type="text" ref="bili" />
  <button @click="handClick">Click Me</button> -->
  <!--Should be same at handClick()-->

  <p>Welcome ...</p>

  <!-- show modal -->
  <!-- instead of using div use teleport to index that has a class called modals -->
  <teleport to="#modals" v-if="showModal">
    <!-- base on property -->
    <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal" /> -->
    <Modal theme="sale" @close="toggleModal">
      <!-- slot -->
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>My First Vue App :v</h1>
      <p>grab your stuff for half price</p>
    </Modal>
  </teleport>

  <teleport to="#modals" v-if="showModal2">
    <Modal @close="toggleModal2">
      <h1>Additional reward</h1>
      <p>Promo code once you login to this page</p>
    </Modal>
  </teleport>

  <!-- toggle modal -->
  <button @click.alt="toggleModal">Open Modal (alt)</button>
  <button @click="toggleModal2">Open Modal</button>

  <!--nested component-->
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";

import Modal from "./components/Modal.vue"; //nested component

export default {
  //VUE JS
  name: "App",
  components: { Modal },
  // components: {
  //   HelloWorld,
  // },
  data() {
    return {
      title: "My First Vue App :v",
      header: "Signup for a Giveaway",
      text: "grab your stuff for half price",
      showModal: false,
      showModal2: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    },
  },
  // methods: {
  //   handClick() {
  //     console.log(this.$refs.bili); //should be same at the button ref
  //     this.$refs.bili.classList.add("active");
  //     this.$refs.bili.focus();
  //   },
  // },
};
</script>

<style>
/* Imported the modal.vue so also inherits the style from it */
#app,
#modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
