<template>
  <q-page class="q-pa-sm">

    <card-dashboard/>

    <card-charts/>

    <div class="row q-col-gutter-sm  q-py-sm">
      <tab-social/>
      <card-with-image/>
    </div>

    <div class="row q-col-gutter-sm  q-pb-sm">
      <todo-list/>

      <card-time-line/>
    </div>

    <table-visits/>
  </q-page>
</template>

<script setup>
import {defineComponent,defineAsyncComponent} from 'vue'
import CardDashboard from 'components/cards/CardDashboard'
import CardCharts from 'components/cards/CardCharts'
</script>