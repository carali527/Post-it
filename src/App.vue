<template>
  <div class="outer-wrap" :style="{
          'background-color': `rgb(${this.red}, ${this.green}, ${this.blue})`,
        }">
    <div class="list" v-for="(item,index) in toDo" :key="index">
        <content-component :item="item"></content-component>
    </div>
    <div class="change-color">
      <p>使用RGB顏色模型來更改背景顏色：</p>
      <color-component v-model:blue="blue" v-model:red="red" v-model:green="green">
        <template v-slot:red>{{ checkRedNumber }}</template>
        <template v-slot:green>{{ checkGreenNumber  }}</template>
        <template v-slot:blue>{{ checkBlueNumber  }}</template>
      </color-component>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ContentComponent from "./components/ContentComponent.vue";
import ColorComponent from "./components/ColorComponent.vue";

export default {
  name: 'App',
  components: {
    ContentComponent,
    ColorComponent
  },
  data() {
    return{
      toDo:[],
      red:"",
      blue:"",
      green:""
    }
  },
  methods: {
    refresh(){
      axios
        .get("https://mocki.io/v1/5c6d8171-d141-4874-8881-ff5b131e1fa1")
        .then((res) => {
          this.toDo = res.data;
        })
        .catch((err) => {
          console.log(err);
        });
    }
  },
  mounted: function() {
    this.refresh() ;
  },
  computed: {
    checkRedNumber() {
      return (this.red >255) ? "can't over 255" : "";
    },
    checkGreenNumber() {
      return (this.green >255) ? "can't over 255" : "";
    },
    checkBlueNumber() {
      return (this.blue >255) ? "can't over 255" : "";
    }
  }
};
</script>

<style>
@import "./assets/css/style.css";
</style>