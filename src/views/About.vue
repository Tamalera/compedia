<template>
  <div class="container">
    <!-- <h2 class="title">Roche</h2> -->
    <div class="columns">
      <div class="column">
        <img
          src="http://commons.wikimedia.org/wiki/Special:FilePath/China%20Construction%20Bank%20logo.svg"
        />
        <div>
          <b-table :data="data" :columns="columns"></b-table>
        </div>
      </div>
      <div class="column"></div>
      <div class="column">
        <div>
          <b-table :data="news" :columns="newsHeader"></b-table>
        </div>
        <div class="shift-down">
          <b-table :data="leaks" :columns="leaksHeader"></b-table>
        </div>
      </div>
    </div>
    <Spider />
  </div>
</template>

<script>
import Spider from "../components/Spider.vue";

export default {
  name: "about",
  components: {
    Spider
  },
  data() {
    return {
      datacollection: null,
      data: [
        {
          id: "Forbes Global 2000 Label",
          facts: "China Construction Bank"
        },
        {
          id: "Country",
          facts: "People's Republic of China"
        },
        {
          id: "Assets",
          facts: "18349489000000"
        },
        {
          id: "Revenues",
          facts: "973502000000"
        },
        {
          id: "#Employees",
          facts: "369183"
        },
        {
          id: "CEO",
          facts: "Wang Hongzhang"
        }
      ],
      columns: [
        {
          field: "id",
          label: "",
          width: "40"
        },
        {
          field: "facts",
          label: ""
        }
      ],
      news: [
        {
          news:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        },
        {
          news:
            "Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
        }
      ],
      newsHeader: [
        {
          field: "news",
          label: "News"
        }
      ],
      leaks: [
        {
          leaks:
            "CEO wears pink socks to official Christmas dinner with key stakeholders."
        }
      ],
      leaksHeader: [
        {
          field: "leaks",
          label: "Leaks"
        }
      ]
    };
  },
  mounted() {
    this.fillData();
  },
  methods: {
    fillData() {
      this.datacollection = {
        labels: [this.getRandomInt(), this.getRandomInt()],
        datasets: [
          {
            label: "Data One",
            backgroundColor: "#f87979",
            data: [this.getRandomInt(), this.getRandomInt()]
          },
          {
            label: "Data One",
            backgroundColor: "#f87979",
            data: [this.getRandomInt(), this.getRandomInt()]
          }
        ]
      };
    },
    getRandomInt() {
      return Math.floor(Math.random() * (50 - 5 + 1)) + 5;
    }
  }
};
</script>

<style scoped>
.shift-down {
  margin-top: 16px;
}
</style>
