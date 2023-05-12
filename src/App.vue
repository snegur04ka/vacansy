<script>
import JobItem from "./components/JobItem.vue";
export default {
  components: { JobItem },
  data() {
    return {
      jobs: [
        {
          id: 0,
          title: "Front-End developer",
          company: "AndroMedia",
          featured: true,
          avatarUrl:
            "https://pinpku.umsida.ac.id/wp-content/uploads/2021/11/andromedia-150x150.png",
          conditions: ["1d ago", "full Time", "Remote"],
          tags: ["HTML", "CSS", "Python", "Vue"],
        },
        {
          id: 1,
          title: "Back-End developer",
          company: "MadDevs",
          featured: false,
          avatarUrl:
            "https://yt3.ggpht.com/a/AGF-l7_0hk3mv6ab2wsBCKlLKCfnvWQhAoHlv9NSmw=s900-c-k-c0xffffffff-no-rj-mo",
          conditions: ["1d ago", "full Time", "KG Only"],
          tags: ["HTML", "CSS", "JS", "Vue"],
        },
        {
          id: 2,
          title: "DevOps developer",
          company: "MadDevs",
          featured: true,
          avatarUrl:
            "https://yt3.ggpht.com/a/AGF-l7_0hk3mv6ab2wsBCKlLKCfnvWQhAoHlv9NSmw=s900-c-k-c0xffffffff-no-rj-mo",
          conditions: ["1d ago", "full Time", "KG Only"],
          tags: ["Django", "Python", "NOdeJS", "Vue"],
        },
      ],
      filteredJobs: [],
      searchText: "",
    };
  },
  methods: {
    filterTags(tag) {
      this.filteredJobs = this.jobs.filter((item) => item.tags.includes(tag));
    },
    filterConditions(text) {
      this.filteredJobs = this.jobs.filter((item) =>
        item.conditions.includes(text)
      );
    },
    searchFilter() {
      this.filteredJobs = this.jobs.filter((item) =>
        item.title.toLowerCase().includes(this.searchText.toLowerCase())
      );
      this.searchText = "";
    },
    featured() {
      this.filteredJobs = this.jobs.filter((item) => item.featured === true);
    },
    setFilterJobs() {
      this.filteredJobs = this.jobs;
    },
    sort() {
      this.filteredJobs = this.filteredJobs.slice().sort((a, b) => {
        if (a.title > b.title) return 1;
        if (a.title == b.title) return 0;
        if (a.title < b.title) return -1;
      });
    },
  },
  mounted() {
    this.setFilterJobs();
  },
};
</script>


<template>
  <header class="header"></header>
  <section class="job">
    <div class="container">
      <button @click="setFilterJobs">ВЕРНУТЬ</button>
      <input v-model="searchText" type="text" placeholder="ВВЕДИТЕ НАЗВАНИЕ" />
      <button @click="searchFilter">НАЙТИ</button>
      <button @click="sort">СОРТИРОВКА</button>
      <div class="job__content">
        <JobItem
          @artem="featured"
          @kot="filterConditions"
          @myshyk="filterTags"
          v-for="job in filteredJobs"
          :key="job.id"
          :job="job"
        />
      </div>
    </div>
  </section>
</template>


<style>
@import url(./css/index.css);
</style>
