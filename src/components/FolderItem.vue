<template>
  <div class="folder">
    <div class="folder__item" :style="styleObject">
      <b>{{ folderName }}</b>
      <form class="form" @submit.prevent>
        <input v-model="newFolderName" class="form__input" />
        <button class="form__button" @click="onClick">
          +
        </button>
      </form>
    </div>

    <div
      v-for="(subFolders, index) in subFolders"
      :key="index"
    >
      <FolderItem
        :subFolders="subFolders.subFolders"
        :folderName="subFolders.folderName"
        :level="level + 1"
      />

    </div>
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
        // add margin for tree to make it actually look like a tree
        marginLeft: `${this.level * 100}px`,
      },
      newFolderName: '',
    };
  },
  methods: {
    onClick() {
      const trimmedValue = this.newFolderName.trim();
      // if the input value contains something meaningful
      if (trimmedValue) {
        // unshift new subfolder
        this.subFolders.unshift({
          folderName: trimmedValue,
          subFolders: [],
        });
        // and clear the input
        this.newFolderName = '';
      }
    },
  },
};
</script>

<style lang="less">
.folder {
  text-align: left;
  color: #2c3e50;
  margin: 10px 0;
}

.form {
  display: flex;

  &__input {
    margin: 0;
    padding: 0 10px;
    color: rgba(midnightblue, .7);
    background-color: transparent;
    border: 2px solid midnightblue;
    border-radius: 6px;
    font-size: 18px;
    font-weight: 700;
    width: 150px;
    height: 40px;
    outline: none;
  }

  &__button {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 2px solid midnightblue;
    border-radius: 6px;
    background-color: transparent;
    color: midnightblue;
    width: 40px;
    height: 40px;
    padding: 0;
    margin: 0 10px;
    font-size: 16px;
    font-weight: 700;
    text-transform: uppercase;
    transition: all .5s ease-in;
    outline: none;
    cursor: pointer;
    overflow: hidden;
  }
}
</style>
