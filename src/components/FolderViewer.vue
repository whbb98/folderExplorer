<template>
  <div>
    <ul v-for="(item, key) in pathObj" :key="key">
      <folder-item :folder="item" :name="key" :isOpen="true" />
    </ul>
  </div>
</template>

<script>
import FolderItem from "./FolderItem.vue";
export default {
  components: {
    FolderItem,
  },
  props: {
    pathObj: {
      required: true,
    },
  },
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    toggleOpen() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style scoped></style>
