<template>
  <div class="home">
    <ModalDialog v-show="isModalVisible" @close="closeModal">
      <template> This is a new modal header</template>
    </ModalDialog>
    <button type="button" class="btn" @click="showModal">Show Modal</button>
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
    isModalVisible: false,
  }),

  methods: {
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
  },
};
</script>
