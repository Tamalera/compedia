<template>
  <div class="container">
    <h1 class="title">Corpedia</h1>
    <b-field>
      <b-input v-model="search"></b-input>
    </b-field>
    <b-button type="is-primary" @click="goToDetailPage(search)"
      >Search</b-button
    >
    <div>
      <ul>
        <li v-for="qCode in qCodes" :key="qCode['id']">ID {{ qCode["id"] }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HelloWorld",
  data: function() {
    return {
      search: "",
      qCodes: {}
    };
  },
  methods: {
    goToDetailPage(search) {
      axios
        .get(
          "https://www.wikidata.org/w/api.php?action=wbsearchentities&search=" +
            search +
            "&format=json&origin=*&language=en&uselang=en&type=item"
        )
        .then(response => (this.qCodes = response.data.search));
      /* this.$router.push({name: 'about', params: { id: this.search }}); */
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
