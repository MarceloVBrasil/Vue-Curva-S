<template>
  <div class="legenda-container">
    <p class="legenda">
      <span class="cor-legenda projetada"></span> % do budget gasto (projeção)
    </p>
    <p class="legenda">
      <span class="cor-legenda real"></span> % do budget gasto (real)
    </p>
  </div>
  <div class="grafico-container">
    <Line :data="chartData.data_projetada" class="grafico" />
    <Line :data="chartData.data_real" class="grafico" />
  </div>
</template>

<script setup lang="ts">
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend,
} from "chart.js";
import { Line } from "vue-chartjs";
import * as chartConfig from "@/data/curvaSData";
import { ref } from "vue";

ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title
  // Tooltip
);

const chartData = ref(chartConfig);
</script>

<style scoped>
.grafico-container {
  position: relative;
}

.grafico {
  position: absolute;
}

.legenda-container {
  display: flex;
  justify-content: center;
  gap: 2rem;
}

.legenda {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  display: flex;
  align-items: center;
  gap: 0.25rem;
}

.cor-legenda {
  width: 10px;
  height: 10px;
  border-radius: 50%;
}

.projetada {
  background-color: #ccc;
}

.real {
  background-color: #000;
}

@media screen and (width < 550px) {
  .legenda-container {
    flex-direction: column;
    align-items: center;
    gap: 0.1rem;
  }
}
</style>
