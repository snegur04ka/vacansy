<template>
  <ul class="job__details flex">
    <li v-for="item in conditions" :key="item" class="job__detail">
      <a @click="handleClickk(item)" href="#" class="job__condition"> {{ item }}</a>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["conditions"],
  methods: {
    handleClickk(text) {
      this.$emit("kot", text);
    },
  },
};
</script>

<style>
</style>