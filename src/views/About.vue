<template>
  <div class="container">
    <!-- <h2 class="title">Roche</h2> -->
    <div class="columns">
      <div class="column">
        <img
          src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Hoffmann-La_Roche_logo.svg/1200px-Hoffmann-La_Roche_logo.svg.png"
        />
        <div>
          <b-table :data="data" :columns="columns"></b-table>
        </div>
      </div>
      <div class="column">
        <radar :chart-data="datacollection"></radar>
      </div>
      <div class="column">
        <div>
          <b-table :data="news" :columns="newsHeader"></b-table>
        </div>
        <div class="shift-down">
          <b-table :data="leaks" :columns="leaksHeader"></b-table>
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
          facts: "Pharmaceutical"
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
          facts: "94'442"
        },
        {
          id: "CEO",
          facts: "Severin Schwan"
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
            "Antitrust reviews delay Roche's Spark deal further, but where are investors?"
        },
        {
          news: "Roche übernimmt US-Biotech-Firma Promedior"
        },
        {
          news:
            "Roches Jungbrunnen sprudelt munter. Das Medikamentenportfolio wird sich in den kommenden Jahren erheblich verändern. Die Gewissheit, dass die Patentklippe umschifft wird, nimmt zu."
        },
        {
          news:
            "Roche says Tecentriq cocktail helps liver cancer patients live longer"
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
            "Roches' CEO wears pink socks to official Christmas dinner with key stakeholders."
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
