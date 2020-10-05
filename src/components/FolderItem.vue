<template>
  <div class="folder-item">
    <div :style="styleObject">
      {{ folderName }}
      <button @click="onClick">
        +
      </button>
    </div>

    <FolderItem
      v-for="(subFolders, index) in subFolders"
      :key="index"
      :subFolders="subFolders.subFolders"
      :folderName="subFolders.folderName"
      :level="level + 1"
    />
  </div>
</template>

<script>
export default {
  name: 'FolderItem',
  props: {
    folderName: String,
    subFolders: Array,
    level: Number,
  },
  data() {
    return {
      styleObject: {
        marginLeft: `${this.level * 100}px`,
        display: 'flex',
      },
    };
  },
  methods: {
    onClick() {
      this.subFolders.unshift({
        folderName: 'Folder',
        subFolders: [],
      });
    },
  },
};
</script>
