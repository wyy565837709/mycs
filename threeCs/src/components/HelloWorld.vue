<template>
  <div id="gaineChild"></div>
</template>

<script>
import * as Three from "three";
export default {
  data() {
    return {
      scene: null, //场景
      camera: null, //相机
      renderer: null, //渲染
      maeh: null //构造组件
    };
  },
  methods: {
    init() {
      //1.获取盒子
      let gaineChild = document.getElementById("gaineChild");
      //2.场景
      this.scene = new Three.Scene();
      //3.相机
      this.camera = new Three.PerspectiveCamera(
        45,
        gaineChild.clientWidth / gaineChild.clientHeight,
        0.1,
        1000
      );
      this.camera.position.set(0,0,30)
      this.scene.add(this.camera)
      //4渲染器
      this.renderer=new Three.WebGLRenderer()
      this.renderer.setSize(gaineChild.clientWidth,gaineChild.clientHeight)
      
      gaineChild.appendChild(this.renderer.domElement)
    },
    animate() {
      requestAnimationFrame(this.animate)
      this.renderer.render(this.scene,this.camera)
    }
  },
  mounted(){
    this.init()
    this.animate() 
  }
};
</script>

<style lang="scss" scoped>
#gaineChild {
  height: 300px;
}
</style>