<script>
import { Line, mixins } from "vue-chartjs";
const { reactiveProp } = mixins;
export default {
  extends: Line,
  mixins: [reactiveProp],
  props: {
    title: {
      type: String
    }
  },
  data() {
    return {
      options: {
        maintainAspectRatio: false,
        responsive: true,
        layout: {
          padding: {
            left: 0,
            right: 0,
            top: 0,
            bottom: 0
          }
        },
        scales: {
          xAxes: [
            {
              display: true,
              time: {
                unit: "date"
              },
              ticks: {
                maxTicksLimit: 24
              },
              gridLines: {
                color: "rgba(0, 0, 0, 0)"
              }
            }
          ],
          yAxes: [
            {
              display: true,
              ticks: {
                beginAtZero: true,
                max: 150000,
                suggestedMax: 150000,
                min: 0,
                suggestedMin: 0,
                stepSize: 25000,
                maxTicksLimit: 10
              },
              gridLines: {
                color: "rgba(0, 0, 0, 0)"
              }
            }
          ]
        },
        title: {
          display: true,
          text: this.title
        },
        legend: {
          display: false
        }
      }
    };
  },
  mounted() {
    this.renderChart(this.chartData, this.options);
  }
};
</script>
