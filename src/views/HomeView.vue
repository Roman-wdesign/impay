<template>
  <div class="home">
    <button @click="showModal">show modal</button>
    <ModalDialog ref="confirmModal">
     <p>Are you sure?</p>
      <template #actions="{confirm}">
        <button @click="confirm" type="button" class="btn-simple" :disabled="isConfirmationCorrect">OK</button>
      </template>

      <template #reject="{close}">
        <button @click="close" type="button" class="btn-close" :disabled="isConfirmationReject">Cancel</button>
      </template>
    </ModalDialog>
  </div>
</template>

<script>
import ModalDialog from "@/components/ModalDialog.vue";

export default {
  name: "HomeView",
  components: {
    ModalDialog,
  },


  data: () => ({
    confirmation: null,
    CONFIRMATION_TEXT: "OK",
    REJECT_TEXT: "CANCEL",
  }),



  //buttons validations
  computed: {
    isConfirmationCorrect() {
      return this.confirmation === this.CONFIRMATION_TEXT;
    },
    isConfirmationReject() {
      return this.confirmation === this.REJECT_TEXT;
    },
  },


  methods: {
    async showModal() {
      //ModalDialog component opens itself on click
      const modalResult = await this.$refs.confirmModal.show();

      if (modalResult) {
        alert("Confirmed!");
      } else {
        alert("Declined!")
      }
    },
  },
};
</script>
<style>
.home {
  margin-top: 2rem;
}

.btn-close {
  cursor: pointer;
  background-color: #af4f4c; /* Red */
  border: none;
  color: white;
  padding: 5px 10px;
  margin: 5px 0;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
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