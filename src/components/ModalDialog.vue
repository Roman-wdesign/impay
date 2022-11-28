<template>
  <div v-if="isOpen" class="modal-backdrop" @click="close">
    <div class="modal" @click.stop>

      <slot></slot>

      <div class="modal-header">
        <slot name="actions" :close="close" :confirm="confirm">
          <button  @click="confirm">Ok</button>
        </slot>

        <slot name="reject" :close="close">
          <button type="button"  @click="close">Отмена</button>
        </slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {

  //initial reactive state
  data: () => ({
    isOpen: false,
    currentModalController: null,
    modalController:null,
  }),

  methods: {

    //  show Modal
    show() {
      let resolve;
      let reject;
      const modalPromise = new Promise((ok, fail) => {
        resolve = ok;
        reject = fail;
      });

      this.modalController = {resolve, reject};
      this.isOpen = true;
      // to modalResult
      return modalPromise;
    },

    confirm() {
      this.modalController.resolve(true);
      this.isOpen = false;
    },

    close() {
      this.modalController.resolve(false);
      this.isOpen = false;
    },
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
</style>
