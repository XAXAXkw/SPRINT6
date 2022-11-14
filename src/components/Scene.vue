<template>
  <div>
    <ul>
      <li
        v-for="(item, i) in PICS"
        :key="i"
        :class="{ active: i === currentSentence }"
      >
        {{ item.txt }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Scene",
  props: {
    currentSentence: { type: Number, required: true },
    PICS: { type: Array, required: true },
  },
  methods: {
    selectItem(currentSentence) {
      this.activeItem = currentSentence;
    },
    data() {
      return {
        activeItem: null,
        currentSentence,
      };
    },
  },
};
</script>

<style lang="css" scoped>
* {
  margin-top: 200px;
}
.active {
  background-color: rgb(29, 217, 255);
  color: blue;
  padding: 15px;
}

li {
  color: white;
  list-style: none;
  margin: 5px;
  padding: 5px;
  border-radius: 35px;
  border: solid 1px blue;
  background-color: rgba(240, 248, 255, 0.333);
}
</style>
