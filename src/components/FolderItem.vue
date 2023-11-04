<template>
  <ul v-show="isOpen">
    <div class="folder-name" @click="toggleCollapse">
      <strong>{{ name }}</strong>
    </div>
    <li v-show="!isCollapsed" v-if="Object.keys(folder).length === 0">/</li>
    <div v-show="!isCollapsed" v-if="Array.isArray(folder)" class="content">
      <div v-for="item in folder">
        <li>{{ item }}</li>
      </div>
    </div>
    <div v-else v-for="(item, key) in folder">
      <folder-item :isOpen="!isCollapsed" :folder="item" :name="key" />
    </div>
  </ul>
</template>

<script>
export default {
  props: {
    isOpen: {
      required: true,
    },
    folder: {
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      isCollapsed: true,
    };
  },
  methods: {
    toggleCollapse(ev) {
      const ul = ev.target.closest("ul");
      if (!this.isCollapsed) {
        Object.values(ul.querySelectorAll("div")).map((el, idx, list) => {
          if (idx !== 0) {
            el.style.display = "none";
          }
        });
        this.isCollapsed = !this.isCollapsed;
      } else {
        Object.values(ul.querySelectorAll("div")).map((el, idx, list) => {
          if (idx !== 0) {
            el.style.display = "block";
          }
        });
        this.isCollapsed = !this.isCollapsed;
      }
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
}
ul li {
  padding: 5px;
}
.folder-name {
  cursor: pointer;
  width: fit-content;
}
.folder-name:hover{
  background-color: #888;
}
</style>
