<template>
  <div class="container">
    <h1 class="title">Corpedia</h1>
    <b-field>
      <b-input v-model="search"></b-input>
    </b-field>
    <b-button type="is-primary" @click="goToDetailPage">Search</b-button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data: function() {
    return {
      search: ""
    };
  },
  methods: {
    goToDetailPage() {
      this.$router.push("about");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
