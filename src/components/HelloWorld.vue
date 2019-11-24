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
      <ol class="gradient-list">
        <li v-for="qCode in qCodes" :key="qCode['id']">
          <router-link :to="{ name: 'about', params: { id: qCode['id'] } }"
            >ID {{ qCode["id"] }}</router-link
          >
        </li>
      </ol>
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
<style scoped lang="scss">
$white: #fafafa;

/*** EXTEND ***/
/* box-shadow */
%boxshadow {
  box-shadow: 0.25rem 0.25rem 0.6rem rgba(0, 0, 0, 0.05),
    0 0.5rem 1.125rem rgba(75, 0, 0, 0.05);
}

/*** STYLE ***/
*,
*:before,
*:after {
  box-sizing: border-box;
}

html,
body {
  margin: 0;
  padding: 0;
}

body {
  background-color: $white;
}

main {
  display: block;
  margin: 0 auto;
  max-width: 40rem;
  padding: 1rem;
}

ol.gradient-list {
  counter-reset: gradient-counter;
  list-style: none;
  margin: 1.75rem 0;
  padding-left: 1rem;
  > li {
    background: white;
    border-radius: 0 0.5rem 0.5rem 0.5rem;
    @extend %boxshadow;
    counter-increment: gradient-counter;
    margin-top: 1rem;
    min-height: 3rem;
    padding: 1rem 1rem 1rem 3rem;
    position: relative;
    &::before,
    &::after {
      border-radius: 1rem 1rem 0 1rem;
      content: "";
      height: 3rem;
      left: -1rem;
      overflow: hidden;
    }
  }
}
</style>
