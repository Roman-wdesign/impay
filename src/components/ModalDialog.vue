<template>
  <div class="modal-backdrop">
    <div class="modal" >
      <header class="modal-header">
        <button type="button" class="btn-close" @click="close">x</button>

        <slot> default header </slot>

        <button type="button" class="btn-simple" @click="close">OK</button>
        <button type="button" class="btn-simple" @click="close">Cancel</button>
      </header>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  methods: {
    //emitting event to HomeView.vue
    close() {
      this.$emit("close");
    },
    show() {},
  },
};
</script>

<style>
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  background: #ffffff;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
  z-index: 10000;
}

.modal-header {
  padding: 25px;
  display: flex;
  flex-direction: column;

  position: relative;
  border-bottom: 1px solid #eeeeee;
  justify-content: space-between;
}

.btn-close {
  position: absolute;
  top: 0;
  right: 0;
  border: none;
  font-size: 20px;
  padding: 10px;
  cursor: pointer;
  font-weight: bold;
  color: #4aae9b;
  background: transparent;
}

.btn-green {
  color: white;
  background: #4aae9b;
  border: 1px solid #4aae9b;
  border-radius: 2px;
}
.btn-simple {
  cursor: pointer;
  background-color: #4caf50; /* Green */
  border: none;
  color: white;
  padding: 5px 10px;
  margin: 5px 0;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
</style>
