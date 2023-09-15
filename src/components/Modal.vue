<template>
  <!-- MODAL VUE reusable in the app vue where you can use multiple modals in just one modal -->

  <!-- .self prevent closing when clicking inside the modal -->
  <div class="backdrop" @click.self="closeModal">
    <!-- passing data in component -->
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <!-- base on property 
        <h1>{{ header }}</h1>
      <p>{{ text }}</p> -->

      <!-- base on Slot -->
      <slot>default content</slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // props: ["header", "text", "theme"], //passing header prop from app.vue to this file
  props: ["theme"], //Slot
  methods: {
    closeModal() {
      this.$emit("close"); //emit modal @close to the app.vue to use toggleModal
    },
  },
};
</script>


<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal h1 {
  color: cyan;
  display: inline-block;
  padding-bottom: block;
}

.modal p {
  font-style: normal;
}

.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
}

.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px white solid;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}

.modal .actions {
  color: white;
}
.modal .actions a {
  color: white;
}

.modal.sale {
  background-color: crimson;
  color: white;
}

.modal.sale h1 {
  color: wheat;
}
</style>