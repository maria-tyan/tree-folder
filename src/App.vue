<template>
  <div id="app">
    <h1>Tree Folder Structure</h1>
    <div
      v-for="(folder, index) in data"
      :key="index"
    >
      <FolderItem
        :folderName="folder.folderName"
        :subFolders="folder.subFolders"
        :level="0"
      />
    </div>
  </div>
</template>

<script>
import FolderItem from './components/FolderItem.vue';

export default {
  name: 'App',
  components: {
    FolderItem,
  },
  data() {
    return {
      // data format is nested objects with properties: folderName and subFolders
      data: [
        {
          folderName: 'Folder1',
          subFolders: [
            {
              folderName: 'Folder2',
              subFolders: [],
            },
            {
              folderName: 'Folder3',
              subFolders: [
                {
                  folderName: 'Folder4',
                  subFolders: [],
                },
              ],
            },
            {
              folderName: 'Folder5',
              subFolders: [],
            },
          ],
        },
        {
          folderName: 'Folder6',
          subFolders: [],
        },
        {
          folderName: 'Folder7',
          subFolders: [
            {
              folderName: 'Folder8',
              subFolders: [],
            },
          ],
        },
      ],
    };
  },
};
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: midnightblue;
  margin: 60px;
}

* {
  box-sizing: inherit;
}
</style>
