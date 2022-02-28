<template>
  <q-card>
    <q-card-section>
      <div class="text-h6 text-grey-8">
        {{ data.title }}
      </div>
    </q-card-section>
    <q-separator/>
    <q-card-section>
      {{ data.text }}
    </q-card-section>
  </q-card>
</template>

<script setup>
import {defineComponent,defineAsyncComponent, reactive} from 'vue'
import { axios } from 'src/boot/axios'

const data = reactive({
  title: String,
  text: String,
})

axios.get('getDashboard').then(
  function(res){
    console.log(res)
    data.title = '안녕안녕'
    data.text = '하이하이'
    console.log(data)
  })

</script>
