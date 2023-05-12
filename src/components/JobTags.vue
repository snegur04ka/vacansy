<template>
  <ul class="job__tags flex">
    <li v-for="item in tags" :key="item" class="job__tag">
      <a @click="handleClick(item)" href="#" class="job__link"> {{ item }} </a>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["tags"],
  methods: {
    handleClick(text) {
      this.$emit("myshyk", text);
    },
  },
};
</script>

<style>
</style>