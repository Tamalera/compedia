<script>
import { Radar } from "vue-chartjs";

export default {
  extends: Radar,
  mounted() {
    this.renderChart(
      {
        labels: [
          "Asserts [M CHF]",
          "Revenue [M CHF]",
          "#K Employees",
          "# Sites",
          "Patents",
          "Lawsuits",
          "Subsidiaries"
        ],
        datasets: [
          {
            label: "2018",
            backgroundColor: "rgba(179,181,255,0.2)",
            borderColor: "rgba(179,181,255,1)",
            pointBackgroundColor: "rgba(179,181,198,1)",
            pointBorderColor: "#fff",
            pointHoverBackgroundColor: "#fff",
            pointHoverBorderColor: "rgba(179,181,198,1)",
            data: [29, 48, 94, 75, 68, 24, 44]
          },
          {
            label: "2019",
            backgroundColor: "rgba(255,99,132,0.2)",
            borderColor: "rgba(255,99,132,1)",
            pointBackgroundColor: "rgba(255,99,132,1)",
            pointBorderColor: "#fff",
            pointHoverBackgroundColor: "#fff",
            pointHoverBorderColor: "rgba(255,99,132,1)",
            data: [35, 15, 94, 16, 63, 15, 45]
          }
        ]
      },
      { responsive: true, maintainAspectRatio: false }
    );
  }
};
</script>
