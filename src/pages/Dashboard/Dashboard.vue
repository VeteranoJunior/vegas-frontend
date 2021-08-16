<template>
  <div class="row">
    <!-- Stats Cards -->
    <div class="col-lg-3 col-md-6" v-for="card in statsCards" :key="card.title">
      <stats-card
        :title="card.title"
        :sub-title="card.subTitle"
        :type="card.type"
        :icon="card.icon"
      >
        <div slot="footer" v-html="card.footer"></div>
      </stats-card>
    </div>

    <!-- Menu Inicial -->
    <card type="nav-tabs" xclass="text-center">
      <div slot="header" class="card-header-primary">Featured</div>
      <h4 class="card-title">Special title treatment</h4>
      <div class="container">
        <div class="row">
          <base-button
            class="animation-on-hover mb-5"
            block
            size="lg"
            type="primary"
            @click="abertura"
            >{{caixa}}</base-button
          >
          <div class="col">
            <base-button
              class="animation-on-hover"
              block
              size="lg"
              type="primary"
              >Nova Venda</base-button
            >
            <base-button class="animation-on-hover" block size="lg" type="info"
              >Alterar/Consultar/Cancelar Venda</base-button
            >
            <!-- <base-button
              class="animation-on-hover"
              block
              size="lg"
              type="success"
              >algumcoisa</base-button
            > -->
          </div>

          <div class="col">
            <base-button
              class="animation-on-hover"
              block
              size="lg"
              type="danger"
              >Relatorio de Vendas</base-button
            >
            <base-button
              class="animation-on-hover"
              block
              size="lg"
              type="warning"
              >Estoque</base-button
            >
            <!-- <base-button
              class="animation-on-hover"
              block
              size="lg"
              type="default"
              >Alterar Estoque</base-button
            > -->
          </div>
        </div>
      </div>

      <div slot="footer" class="text-muted">2 days ago</div>
    </card>
  </div>
</template>
<script>
import LineChart from "@/components/Charts/LineChart";
import BarChart from "@/components/Charts/BarChart";
import * as chartConfigs from "@/components/Charts/config";
import TaskList from "./TaskList";
import UserTable from "./UserTable";
import CountryMapCard from "./CountryMapCard";
import StatsCard from "src/components/Cards/StatsCard";
import config from "@/config";

let bigChartData = [
  [100, 70, 90, 70, 85, 60, 75, 60, 90, 80, 110, 100],
  [80, 120, 105, 110, 95, 105, 90, 100, 80, 95, 70, 120],
  [60, 80, 65, 130, 80, 105, 90, 130, 70, 115, 60, 130],
];
let bigChartLabels = [
  "JAN",
  "FEB",
  "MAR",
  "APR",
  "MAY",
  "JUN",
  "JUL",
  "AUG",
  "SEP",
  "OCT",
  "NOV",
  "DEC",
];
let bigChartDatasetOptions = {
  fill: true,
  borderColor: config.colors.primary,
  borderWidth: 2,
  borderDash: [],
  borderDashOffset: 0.0,
  pointBackgroundColor: config.colors.primary,
  pointBorderColor: "rgba(255,255,255,0)",
  pointHoverBackgroundColor: config.colors.primary,
  pointBorderWidth: 20,
  pointHoverRadius: 4,
  pointHoverBorderWidth: 15,
  pointRadius: 4,
};

export default {
  components: {
    LineChart,
    BarChart,
    StatsCard,
    TaskList,
    CountryMapCard,
    UserTable,
  },
  data() {
    return {
      caixa: "Abrir caixa",
      statsCards: [
        {
          title: "150GB",
          subTitle: "Number",
          type: "warning",
          icon: "tim-icons icon-chat-33",
          footer: '<i class="tim-icons icon-refresh-01"></i> Update Now',
        },
        {
          title: "+45K",
          subTitle: "Followers",
          type: "primary",
          icon: "tim-icons icon-shape-star",
          footer: '<i class="tim-icons icon-sound-wave"></i></i> Last Research',
        },
        {
          title: "150,000",
          subTitle: "Users",
          type: "info",
          icon: "tim-icons icon-single-02",
          footer: '<i class="tim-icons icon-trophy"></i> Customer feedback',
        },
        {
          title: "23",
          subTitle: "Errors",
          type: "danger",
          icon: "tim-icons icon-molecule-40",
          footer: '<i class="tim-icons icon-watch-time"></i> In the last hours',
        },
      ],
      bigLineChart: {
        activeIndex: 0,
        chartData: {
          datasets: [
            {
              ...bigChartDatasetOptions,
              data: bigChartData[0],
            },
          ],
          labels: bigChartLabels,
        },
        extraOptions: chartConfigs.purpleChartOptions,
        gradientColors: config.colors.primaryGradient,
        gradientStops: [1, 0.4, 0],
        categories: [],
      },
      purpleLineChart: {
        extraOptions: chartConfigs.purpleChartOptions,
        chartData: {
          labels: ["JUL", "AUG", "SEP", "OCT", "NOV", "DEC"],
          datasets: [
            {
              label: "Data",
              fill: true,
              borderColor: config.colors.primary,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.primary,
              pointBorderColor: "rgba(255,255,255,0)",
              pointHoverBackgroundColor: config.colors.primary,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [80, 100, 70, 80, 120, 80],
            },
          ],
        },
        gradientColors: config.colors.primaryGradient,
        gradientStops: [1, 0.2, 0],
      },
      greenLineChart: {
        extraOptions: chartConfigs.greenChartOptions,
        chartData: {
          labels: ["JUL", "AUG", "SEP", "OCT", "NOV"],
          datasets: [
            {
              label: "My First dataset",
              fill: true,
              borderColor: config.colors.danger,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.danger,
              pointBorderColor: "rgba(255,255,255,0)",
              pointHoverBackgroundColor: config.colors.danger,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [90, 27, 60, 12, 80],
            },
          ],
        },
        gradientColors: [
          "rgba(66,134,121,0.15)",
          "rgba(66,134,121,0.0)",
          "rgba(66,134,121,0)",
        ],
        gradientStops: [1, 0.4, 0],
      },
      blueBarChart: {
        extraOptions: chartConfigs.barChartOptions,
        chartData: {
          labels: ["USA", "GER", "AUS", "UK", "RO", "BR"],
          datasets: [
            {
              label: "Countries",
              fill: true,
              borderColor: config.colors.info,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              data: [53, 20, 10, 80, 100, 45],
            },
          ],
        },
        gradientColors: config.colors.primaryGradient,
        gradientStops: [1, 0.4, 0],
      },
    };
  },
  computed: {
    enableRTL() {
      return this.$route.query.enableRTL;
    },
    isRTL() {
      return this.$rtl.isRTL;
    },
    bigLineChartCategories() {
      return [
        { name: "Accounts", icon: "tim-icons icon-single-02" },
        { name: "Purchases", icon: "tim-icons icon-gift-2" },
        { name: "Sessions", icon: "tim-icons icon-tap-02" },
      ];
    },
  },
  methods: {
    abertura(){
      
      if (this.caixa == "Abrir caixa") {
        this.caixa = "Fechar Caixa"
      } else {
        this.caixa = "Abrir caixa"
      }
      

    },
    initBigChart(index) {
      let chartData = {
        datasets: [
          {
            ...bigChartDatasetOptions,
            data: bigChartData[index],
          },
        ],
        labels: bigChartLabels,
      };
      this.$refs.bigChart.updateGradients(chartData);
      this.bigLineChart.chartData = chartData;
      this.bigLineChart.activeIndex = index;
    },
  },
  mounted() {
    this.i18n = this.$i18n;
    if (this.enableRTL) {
      this.i18n.locale = "ar";
      this.$rtl.enableRTL();
    }
    this.initBigChart(0);
  },
  beforeDestroy() {
    if (this.$rtl.isRTL) {
      this.i18n.locale = "en";
      this.$rtl.disableRTL();
    }
  },
};
</script>
<style></style>
