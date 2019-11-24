<template>
  <div>
    <div v-bind:style="{}">
      <vo-basic
        :data="subsidiary_tree"
        :draggable="false"
        :direction="'l2r'"
      ></vo-basic>
    </div>
  </div>
</template>

<script>
import { VoBasic } from "vue-orgchart";
import "vue-orgchart/dist/style.min.css";

export default {
  components: {
    VoBasic
  },
  props: ["subsidiary_tree"],
  data() {
    console.log(this.subsidiary_tree);
    return {
      ds: this.subsidiary_tree,
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
  }
};
</script>
