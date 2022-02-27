<template>
  <q-card class="bg-transparent no-shadow no-border">
    <q-card-section class="q-pa-none">
      <div class="row q-col-gutter-sm ">
        <div v-for="(item, index) in data.items" :key="index" class="col-md-6 col-sm-12 col-xs-12">
          <q-item :style="`background-color: ${item.color1}`" class="q-pa-none">
            <q-item-section side :style="`background-color: ${item.color2}`"
                            class=" q-pa-lg q-mr-none text-white">
              <q-icon :name="item.icon" color="white" size="24px"></q-icon>
            </q-item-section>
            <q-item-section class=" q-pa-md q-ml-none  text-white">
              <q-item-label>{{ item.title }}</q-item-label>
              <q-item-label class="text-white text-h6 text-weight-bolder">{{ item.value }}</q-item-label>
            </q-item-section>
          </q-item>
        </div>
      </div>
    </q-card-section>
  </q-card>
</template>

<script setup>
import {defineComponent,defineAsyncComponent, reactive} from 'vue'
import { axios } from 'src/boot/axios'

const data = reactive({
  items: Array
})
axios.get('getDashboard').then(
  function(res){
    data.items = [
              {
                title: "오늘의 말씀",
                icon: "book",
                value: res.data.verse,
                color1: "#5064b5",
                color2: "#3e51b5"
              },
              {
                title: "오늘 큐티 적용",
                icon: "done",
                value: res.data.apply,
                color1: "#f37169",
                color2: "#f34636"
              },
              {
                title: "나의 기도제목",
                icon: "favorite",
                value: res.data.prayer,
                color1: "#ea6a7f",
                color2: "#ea4b64"
              },
              {
                title: "이번주 큐티",
                icon: "bar_chart",
                value: "5일 중 4번",
                color1: "#a270b1",
                color2: "#9f52b1"
              }
            ]
  })

</script>
