<template>
  <div>
    <v-container fluid>
      <v-row justify="center">
        <v-col cols="12" md="6">
          <v-row justify="center">
            <v-col cols="12" md="12">
              <v-btn depressed color="primary" @click="randomData()">
                Random Data
              </v-btn>
            </v-col>

            <v-col cols="12" md="6">
              <v-card>
                <div class="chart-area pt-4">
                  <barChart
                    v-if="flagInit"
                    :title="'Ingresos de la semana'"
                    :width="200"
                    :height="250"
                    :chart-data="datacollection[0]"
                  />
                </div>
              </v-card>
            </v-col>

            <v-col cols="12" md="6">
              <v-card>
                <div class="chart-area pt-4">
                  <barChart
                    v-if="flagInit"
                    :title="'Gastos de la semana'"
                    :width="200"
                    :height="250"
                    :chart-data="datacollection[1]"
                  />
                </div>
              </v-card>
            </v-col>
            <v-col cols="12" md="12">
              <v-card>
                <div class="chart-area pt-4">
                  <lineChart
                    v-if="flagInit"
                    :title="'Ingresos por hora del dia'"
                    :width="200"
                    :height="250"
                    :chart-data="datacollection[2]"
                  />
                </div>
              </v-card>
            </v-col>
          </v-row>
        </v-col>

        <v-col cols="12" md="6">
          <dataTable />
        </v-col>
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
      flagInit: false,
      datacollection: []
    };
  },
  methods: {
    randomData() {
      this.datacollection = [];
      let r_color = () => (Math.random() * 256) >> 0;
      for (let index = 0; index < 3; index++) {
        index != 2
          ? this.datacollection.push({
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
                    `rgb(${r_color()}, ${r_color()}, ${r_color()})`,
                    `rgb(${r_color()}, ${r_color()}, ${r_color()})`,
                    `rgb(${r_color()}, ${r_color()}, ${r_color()})`,
                    `rgb(${r_color()}, ${r_color()}, ${r_color()})`,
                    `rgb(${r_color()}, ${r_color()}, ${r_color()})`,
                    `rgb(${r_color()}, ${r_color()}, ${r_color()})`,
                    `rgb(${r_color()}, ${r_color()}, ${r_color()})`
                  ],
                  pointBorderColor: "#2554FF",
                  data: Array.from(Array(7)).map(x =>
                    Math.floor(Math.random() * (150001 - 25001) + 25001)
                  )
                }
              ]
            })
          : this.datacollection.push({
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
                  label: "Line Chart",
                  borderWidth: 1,
                  borderColor: `rgb(${r_color()}, ${r_color()}, ${r_color()})`,
                  pointBorderColor: `rgb(${r_color()}, ${r_color()}, ${r_color()})`,
                  backgroundColor: `rgb(${r_color()}, ${r_color()}, ${r_color()})`,
                  data: Array.from(Array(24)).map(x =>
                    Math.floor(Math.random() * (150001 - 25001) + 25001)
                  )
                }
              ]
            });
      }

      this.flagInit = true;
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
