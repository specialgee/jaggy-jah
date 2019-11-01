<template>
  <div id="home">
    <!--
    <video autoplay muted loop id="video">
      <source src="../assets/mov/smoke.mp4" type="video/mp4">
    </video>
    -->

    <div id="container"></div>

    <div id="overlay">
      <div class="wrapper">
        <h1 id="title" class="animated infinite rubberBand">
          JAGGY<br>
          JAH
        </h1>
      </div>
    </div>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#container {
    width: 100vw;
    height: 100vh;
    margin: 0 auto;
    position: absolute;
    top: 0px;
    left: 0px;
}
</style>

<script>
import * as THREE from 'three';

export default {
  name: 'Home',
  props: {
    msg: String
  },
  data() {
    return {
      camera: null,
      scene: null,
      renderer: null,
      mesh: null
    }
  },
  methods: {
    init: function() {
        let container = document.getElementById('container');

        this.camera = new THREE.PerspectiveCamera(70, container.clientWidth/container.clientHeight, 0.01, 10);
        this.camera.position.z = 1;

        this.scene = new THREE.Scene();

        let geometry = new THREE.BoxGeometry(0.2, 0.2, 0.2);
        let material = new THREE.MeshNormalMaterial();

        this.mesh = new THREE.Mesh(geometry, material);
        this.scene.add(this.mesh);

        var body = document.body;
        var backgroundColor = window.getComputedStyle(body, null).getPropertyValue("background-color");

        this.renderer = new THREE.WebGLRenderer({antialias: true, alpha: true});
        this.renderer.setSize(container.clientWidth, container.clientHeight);
        this.renderer.setClearColor(backgroundColor, 0.8);
        container.appendChild(this.renderer.domElement);

    },
    animate: function() {
        requestAnimationFrame(this.animate);
        this.mesh.rotation.x += 0.01;
        this.mesh.rotation.y += 0.02;
        this.renderer.render(this.scene, this.camera);
    }
  },
  mounted() {
      this.init();
      this.animate();
  }
}

</script>