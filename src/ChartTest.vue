<script>
import { Bar, mixins } from "vue-chartjs";

export default {
  extends: Bar,
  mixins: [mixins.reactiveProp],
  props: ["options"],
  mounted() {
    console.log("ChartTest mount!!");
    console.log("ChartTest", this.chartData);
    console.log("ChartTest", this.options);
    this.renderChart(this.chartData, this.options);
  },
};
</script>

<style></style>
