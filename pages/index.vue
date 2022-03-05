<template>
  <div>
    <v-system-bar height="56" dark color="primary"></v-system-bar>
    <v-btn depressed color="primary" @click="randomData()">
      Random Data
    </v-btn>
    <v-container fluid>
      <v-row justify="center">
        <v-col cols="12" md="4">
          <v-card>
            <div class="chart-area pt-4">
              <barChart
                :title="'Ingresos de la semana'"
                :width="200"
                :height="250"
                :chart-data="datacollection[0]"
              />
            </div>
          </v-card>
        </v-col>

        <v-col cols="12" md="4">
          <v-card>
            <div class="chart-area pt-4">
              <barChart
                :title="'Gastos de la semana'"
                :width="200"
                :height="250"
                :chart-data="datacollection[1]"
                :titleName="Prueba"
              />
            </div>
          </v-card>
        </v-col>

        <v-col cols="12" md="12">
          <v-card>
            <div class="chart-area pt-4">
              <lineChart
                :title="'Ingresos por hora del dia'"
                :width="200"
                :height="250"
                :chart-data="datacollection[2]"
              />
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>

    <v-container fluid>
      <v-row justify="center">
        <dataTable />
      </v-row>
    </v-container>
  </div>
</template>

<script>
import barChart from "../components/bar-chart";
import lineChart from "../components/line-chart";
import dataTable from "../components/datatable";

export default {
  components: {
    barChart,
    lineChart,
    dataTable
  },
  data() {
    return {
      datacollection: [
        {
          labels: [
            "Lunes",
            "Martes",
            "Miercoles",
            "Jueves",
            "Viernes",
            "Sabado",
            "Domingo"
          ],
          datasets: [
            {
              label: "Bar Chart",
              borderWidth: 1,
              backgroundColor: [
                "rgba(255, 99, 132, 0.2)",
                "rgba(54, 162, 235, 0.2)",
                "rgba(255, 206, 86, 0.2)",
                "rgba(75, 192, 192, 0.2)",
                "rgba(153, 102, 255, 0.2)",
                "rgba(255, 159, 64, 0.2)",
                "rgba(255, 99, 132, 0.2)"
              ],
              pointBorderColor: "#2554FF",
              data: [12, 19, 3, 5, 2, 3, 20]
            }
          ]
        },
        {
          labels: [
            "Lunes",
            "Martes",
            "Miercoles",
            "Jueves",
            "Viernes",
            "Sabado",
            "Domingo"
          ],
          datasets: [
            {
              label: "Bar Chart",
              borderWidth: 1,
              backgroundColor: [
                "rgba(255, 99, 132, 0.2)",
                "rgba(50, 162, 245, 0.2)",
                "rgba(255, 206, 86, 0.2)",
                "rgba(475, 192, 192, 0.2)",
                "rgba(153, 102, 255, 0.2)",
                "rgba(220, 159, 64, 0.2)",
                "rgba(255, 99, 132, 0.2)"
              ],
              pointBorderColor: "#2554FF",
              data: [17, 14, 34, 54, 2, 3, 20]
            }
          ]
        },
        {
          labels: [
            "00:00",
            "01:00",
            "02:00",
            "03:00",
            "04:00",
            "05:00",
            "06:00",
            "07:00",
            "08:00",
            "09:00",
            "10:00",
            "12:00",
            "13:00",
            "14:00",
            "15:00",
            "16:00",
            "17:00",
            "18:00",
            "19:00",
            "20:00",
            "21:00",
            "22:00",
            "23:00"
          ],
          datasets: [
            {
              label: "Bar Chart",
              borderWidth: 1,
              backgroundColor: [
                "rgba(255, 99, 132, 0.2)",
                "rgba(54, 162, 235, 0.2)",
                "rgba(255, 206, 86, 0.2)",
                "rgba(75, 192, 192, 0.2)",
                "rgba(153, 102, 255, 0.2)",
                "rgba(255, 159, 64, 0.2)",
                "rgba(255, 99, 132, 0.2)"
              ],
              pointBorderColor: "#2554FF",
              data: [
                12,
                19,
                3,
                5,
                2,
                3,
                20,
                12,
                19,
                3,
                5,
                2,
                3,
                20,
                12,
                19,
                3,
                5,
                2,
                3,
                20,
                78,
                89,
                100
              ]
            }
          ]
        }
      ]
    };
  },
  methods: {
    randomData() {
      this.datacollection.forEach(element => {
        console.log(element.datasets[0]);
        element.datasets[0].data.map((value, index) => {
          element.datasets[0].data[index] = Math.floor(Math.random() * 150001);
        });
      });
    }
  },
  mounted() {
    this.randomData();
  }
};
</script>

<style>
@import "../assets/styles/main.css";
</style>
