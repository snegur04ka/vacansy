<template>
  <div class="job__item flex">
    <div class="job__left flex">
      <div class="job__avatar">
        <img class="img" :src="job.avatarUrl" />
      </div>
      <div class="data">
        <div class="job__top flex">
          <h2 class="job__company">{{ job.company }}</h2>
          <div class="job__featured" @click="featuredClick(job.featured)" v-if="job.featured">featured!</div>
        </div>
        <div class="job__center">
          <h2 class="job__title">{{ job.title }}</h2>
        </div>
        <div class="job__bottom">
          <JobCondition @kot="handleClickk" :conditions="job.conditions" />
        </div>
      </div>
    </div>
    <div class="job__right">
      <JobTags @myshyk="handleClick" :tags="job.tags" />
    </div>
  </div>
</template>

<script>
import JobCondition from "./JobCondition.vue";
import JobTags from "./JobTags.vue";
export default {
  data() {
    return {};
  },
  components: { JobTags, JobCondition },
  props: ["job"],
  methods: {
    handleClick(aga) {
      this.$emit("myshyk", aga);
    },
    handleClickk(text) {
      this.$emit("kot", text);
    },
    featuredClick(test) {
      this.$emit("artem", test);
    },
  },
};
</script>

<style>
</style>