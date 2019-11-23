<template>
  <div class="container">
    <h2 class="title">COMPANY NAME</h2>
    <div class="columns">
      <div class="column">
        <img src="../assets/placeholder.png" />
        <div>
          <b-table :data="data" :columns="columns"></b-table>
        </div>
      </div>
      <div class="column">
        <radar :chart-data="datacollection"></radar>
      </div>
      <div class="column">
        <div>
          <b-menu>
            <b-menu-list label="News">
              <b-menu-item label="News Item 1"></b-menu-item>
              <b-menu-item label="News Item 1"></b-menu-item>
              <b-menu-item label="News Item 1"></b-menu-item>
            </b-menu-list>
          </b-menu>
        </div>
        <div class="shift-down">
          <b-menu>
            <b-menu-list label="Leaks">
              <b-menu-item label="Leak Item 1"></b-menu-item>
              <b-menu-item label="Leak Item 1"></b-menu-item>
              <b-menu-item label="Leak Item 1"></b-menu-item>
            </b-menu-list>
          </b-menu>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Radar from "../components/Radar.vue";

export default {
  name: "about",
  components: {
    Radar
  },
  data() {
    return {
      datacollection: null,
      data: [
        {
          id: "Type",
          facts: "Pfarmaceutical"
        },
        {
          id: "Asset",
          facts: "200M CHF"
        },
        {
          id: "Revenue",
          facts: "500M CHF"
        },
        {
          id: "#Employees",
          facts: "150'000"
        },
        {
          id: "CEO",
          facts: "Pikachu"
        }
      ],
      columns: [
        {
          field: "id",
          label: "Id",
          width: "40"
        },
        {
          field: "facts",
          label: "Fact"
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
