<template>
  <div class="container">
    <plotly
      id="js-plotly-plot"
      :data="dataPoints"
      :layout="layout"
    />
    <div id="fileinput">
      <input type="file" accept="application/json" @change="previewFiles"/>
    </div>
  </div>
</template>

<script>
import { Plotly } from 'vue-plotly';
import dataPoints from '../assets/Dev8_200umgrid.json';

export default {
  name: 'HeatMap',
  components: {
    Plotly,
  },
  data() {
    return {
      inputFile: dataPoints,
      layout: {
        title: 'Besi 3D',
        autosize: true,
        width: null,
        height: null,
        margin: {
          l: 0,
          r: 0,
          b: 0,
          t: 0,
          pad: 0,
        },
      },
    };
  },
  methods: {
    previewFiles(event) {
      if (event.target.files && event.target.files.length === 1) {
        const fr = new FileReader();
        fr.onload = (e) => {
          this.inputFile = JSON.parse(e.target.result);
        };
        fr.readAsText(event.target.files.item(0));
      }
    },
  },
  computed: {
    dataPoints() {
      return [{
        x: this.inputFile.meshgridX,
        y: this.inputFile.meshgridY,
        z: this.inputFile.meshgridZ,
        type: 'surface',
      }];
    },
  },
};
</script>

<style scoped>
.container {
  position: relative;
}
#js-plotly-plot {
  position: absolute;
  top: 30px;
  left: 0;
  width: 100vw;
  height: calc(100vh - 30px);
}
#fileinput {
  position: absolute;
  width: 100%;
  left: 0;
  top: 0;
  background-color: white;
  height: 30px;
  padding-top: 5px;
  text-align: center;
}
</style>
