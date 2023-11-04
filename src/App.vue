<script>
import FolderViewer from "./components/FolderViewer.vue";
export default {
  components: {
    FolderViewer,
  },
  data() {
    return {
      pathObj: {
        Home: {
          Documents: ["document1.pdf", "document2.pdf"],
          Photos: {
            summer: ["photo1.jpg", "photo2.jpg"],
            winter: ["photo3.jpg", "photo4.jpg"],
            family: {
              travel: ["dublin.png", "london.png"],
            },
          },
          Music: {
            rock: ["song1.mp3", "song2.mp3"],
            pop: ["song3.mp3", "song4.mp3"],
          },
          Video: {},
        },
      },
    };
  },
  methods: {
    printDir(folder, space) {
      for (const key in folder) {
        console.log(space + key);
        if (Array.isArray(folder[key])) {
          console.log(space + "\t" + folder[key]);
        } else {
          this.printDir(folder[key], space + "\t");
        }
      }
    },
  },
};
</script>

<template>
  <h1>Viewing Files Recursively !</h1>
  <FolderViewer :pathObj="pathObj" />
  <button @click="printDir(pathObj, '')">Console Log Dir Tree</button>
</template>

<style scoped></style>
