<template>
  <div class="container">
    <div class="columns">
      <div class="column">
        <img
          src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Hoffmann-La_Roche_logo.svg/1200px-Hoffmann-La_Roche_logo.svg.png"
        />
      </div>
      <div class="column">
        Headquarters
        <br />
        <country-flag country="ch" size="normal" />
        <br />Subsidiaries
        <br />
        <country-flag country="it" size="normal" />
        <country-flag country="fr" size="normal" />
        <country-flag country="de" size="normal" />
        <country-flag country="us" size="normal" />
        <country-flag country="gb" size="normal" />
        <country-flag country="cn" size="normal" />
        <country-flag country="in" size="normal" />
        <country-flag country="no" size="normal" />
        <country-flag country="ro" size="normal" />
        <country-flag country="br" size="normal" />
        <country-flag country="eg" size="normal" />
      </div>
      <div class="column">
        94000 Employees
        <br />
        <img
          v-for="index in 9"
          :key="index"
          class="fixed-size"
          src="https://icon-library.net/images/employee-icon-png/employee-icon-png-5.jpg"
        />
        <img />
      </div>
    </div>
    <div class="columns">
      <div class="column">
        <b-table :data="news" :columns="newsHeader"></b-table>
      </div>
      <div class="column">
        <b-table :data="leaks" :columns="leaksHeader"></b-table>
      </div>
      <div class="column">
        <div>
          500 M CHF Assets
          <br />
          <img
            v-for="index in 5"
            :key="index"
            class="fixed-size"
            src="http://cdn.onlinewebfonts.com/svg/img_457529.png"
          />
          <img />
        </div>
        <div>
          3000 M CHF Revenue
          <br />
          <img
            v-for="index in 3"
            :key="index"
            class="fixed-size"
            src="http://cdn.onlinewebfonts.com/svg/img_457529.png"
          />
          <img />
        </div>
        <div>Subsidiaries</div>
        <div>
          <OrgChart v-bind:subsidiary_tree="subsidiary_tree" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CountryFlag from "vue-country-flag";
import axios from "axios";
import OrgChart from "../components/OrgChart";

export default {
  name: "new-design",
  components: {
    CountryFlag,
    OrgChart
  },
  mounted: function() {
    axios
      .get(
        "https://www.wikidata.org/w/api.php?action=wbgetclaims&entity=" +
          "Q212646" +
          "&format=json&origin=*&language=en&uselang=en&type=item"
      )
      .then(response => {
        console.log(response.data.P355);
        const subsidiaries = response.data.claims.P355;
        let Qids = [];
        subsidiaries.forEach(subsidiary => {
          const Qid = subsidiary.mainsnak.datavalue.value.id;
          Qids.push(Qid);
        });

        console.log(response.data);
        const company_name =
          response.data.claims.P373[0].mainsnak.datavalue.value;

        axios
          .get(
            "https://www.wikidata.org/w/api.php?action=wbgetentities&ids=" +
              Qids.join("|") +
              "&props=labels&languages=en&format=json" +
              "&format=json&origin=*&language=en&uselang=en&type=item"
          )
          .then(response => {
            let subsidiary_tree_leaves = [];
            Qids.forEach(Qid => {
              const name = response.data.entities[Qid].labels.en.value;
              subsidiary_tree_leaves.push(name);
              console.log(name);
              console.log(response.data.entities[Qid]);
            });

            const leaves = subsidiary_tree_leaves.map((name, index) => {
              return { id: index, name: name };
            });

            let subsidiary_tree = {
              id: "1",
              name: company_name,
              children: leaves
            };

            this.subsidiary_tree = subsidiary_tree;
          });
      });
  },
  data() {
    return {
      datacollection: null,
      subsidiary_tree: {},
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
  methods: {
    getGraph: function() {}
  }
};
</script>

<style scoped>
.fixed-size {
  width: 24px;
  height: 24px;
}
</style>
