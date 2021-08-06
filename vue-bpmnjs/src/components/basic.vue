<template>
  <div class="container">
    <div class="canvas" ref="canvas"></div>
  </div>
</template>

<script>
import BpmnModeler from "bpmn-js/lib/Modeler";
import xmlStr from "../mock/xmlStr";
export default {
  data() {
    return {
      bpmnModeler: null,
      container: null,
      canvas: null,
    };
  },
  methods: {
    async init() {
      const canvas = this.$refs.canvas;
      //   this.bpmnModeler = new BpmnModeler({
      //     container: canvas,
      //   });
      //   this.createNewDiagram();

      const modeler = new BpmnModeler({
        container: canvas,
      });

      try {
        const result = await modeler.importXML(xmlStr);
        // const { warnings } = result;
        // console.log(warnings);
        console.log("创建成功");
        // result.saveDiagram((err, xml) => {
        //   console.log(xml);
        // });
        // result.on("commandStack.changed", () => {
        //   console.log("变化了");
        // });
      } catch (err) {
        console.log("xml转图片", err.message, err.warnings);
      }

      try {
        const result = await modeler.open(this.container);
        const { warnings } = result;
        console.log(warnings);
      } catch (err) {
        console.log("图片转xml", err.message, err.warnings);
      }
    },
    // createNewDiagram() {
    //   this.bpmnModeler.importXML(xmlStr, (err) => {
    //     console.log("err", err);
    //     if (err) {
    //       console.log(err);
    //     } else {
    //       console.log("创建成功");
    //     }
    //   });
    // },
  },
  mounted() {
    this.init();
  },
};
</script>

<style scoped>
.container {
  background-color: #ffffff;
  width: 100%;
  height: 100%;
}
.canvas {
  width: 100%;
  height: 100%;
}
.panel {
  position: absolute;
  right: 0;
  top: 0;
  width: 300px;
}
</style>

