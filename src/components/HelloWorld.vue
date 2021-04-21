<template>
  <div id="container">
  </div>
</template>

<script>

import * as Three from 'three';

import { OrbitControls } from "three/examples/jsm/controls/OrbitControls";


export default {
  title: 'Sphere Tangents',
  name: 'HelloWorld',
  props: {
    exploded: Boolean,
    simulating: Boolean,
    msg: String
  },
  data() {
    return {
      camera: null,
      scene: null,
      renderer: null,
      mainSphere: null,
      controls: null,
      axesHelper: null,
      gridHelper: null,
      circularMotion:null,
      pointOne: null,
      group: null,
    }
  },
  methods: {
    init: function() {
      let container = document.getElementById('container');

      this.camera = new Three.PerspectiveCamera(70, container.clientWidth/container.clientHeight, 0.01, 50);
      this.camera.position.z = 3.5;
      this.camera.position.y = 3;
      this.camera.position.x = 2;
      this.scene = new Three.Scene();
      let groupie = new Three.Group();

       this.group = groupie;


      // Main Sphere Geometry
      let mainSphereGeo = new Three.SphereGeometry( 1, 32, 32 );
      let mainSphereMaterial = new Three.MeshBasicMaterial( {color: 0x49ef4, opacity:0.64, transparent: true} );
      let mainSphere1 = new Three.Mesh( mainSphereGeo, mainSphereMaterial );
      this.mainSphere = mainSphere1;
      this.mainSphere.position.y = 1.5;
      this.mainSphere.position.x = 0.2;
      this.mainSphere.position.z = -0.18;
      this.group.add(this.mainSphere);

      // Pink Point on Geo
      let pointOneGeo = new Three.SphereGeometry( .03, 32, 32 );
      let pointOneMaterial = new Three.MeshBasicMaterial( {color: '#FFC0CB', opacity:0.64, transparent: false} );
      let pointOne1 = new Three.Mesh( pointOneGeo, pointOneMaterial );
      this.pointOne = pointOne1;
      this.pointOne.position.y = 1.5;
      this.pointOne.position.x = 0;
      this.pointOne.position.z = .8;
      this.group.add(this.pointOne);

      // Torus of Circular Motion
      let circularMotionGeo = new Three.TorusGeometry( .9, 0.01, 19, 100 );
      let circularMotionMaterial = new Three.MeshBasicMaterial( {color: '#ffa500', opacity:0.90, transparent: false} );
      let circularMotion1 = new Three.Mesh( circularMotionGeo, circularMotionMaterial );
      this.circularMotion = circularMotion1;
      this.circularMotion.position.y = 1.5;
      this.circularMotion.position.z = -.1;
      this.circularMotion.rotation.x = 1.5708 ;
      this.group.add(this.circularMotion);

      // Arrow Helper
      let dir = new Three.Vector3( 1, 0, 0 );
//normalize the direction vector (convert to vector of length 1)
      dir.normalize();
      let origin = new Three.Vector3( 0, 1.5, .8 );
      let length = .9;
      let hex = 0xffff00;
      let headLength = .2;
      let headWidth = headLength*.5;
      let arrowHelper = new Three.ArrowHelper( dir, origin, length, hex, headLength, headWidth );
      arrowHelper.line.material.linewidth = 2000;
      console.log(arrowHelper);
      this.group.add( arrowHelper );

      dir = new Three.Vector3( 0, 3.7,2);
//normalize the direction vector (convert to vector of length 1)
      dir.normalize();
      origin = new Three.Vector3( 0, 0, 0 );
      length = 1.7;
      hex = 0xffff00;
      headLength = .2;
      headWidth = headLength*.5;
      arrowHelper = new Three.ArrowHelper( dir, origin, length, hex, headLength, headWidth );
      arrowHelper.line.material.linewidth = 2000;
      console.log(arrowHelper);
      this.group.add( arrowHelper );

      // Rotation 90 Degrees in radians = 1.5708


      this.renderer = new Three.WebGLRenderer({antialias: true});
      this.renderer.setSize(container.clientWidth, container.clientHeight);
      this.controls = new OrbitControls( this.camera, this.renderer.domElement );
      this.controls.maxDistance = 7;
      this.controls.minDistance = 1.3;
      // this.controls.minAzimuthAngle = 3;
      // this.controls.maxAzimuthAngle = 2;
      this.controls.target.set(0,1.5,0);
      this.controls.enablePan = false;
      this.controls.autoRotate = true;
      this.controls.autoRotateSpeed = 0.1;
      this.controls.update();
      this.renderer.setClearColor('#000000');




      this.scene.add( this.group );

      this.gridHelper = new Three.GridHelper( 50, 50 );
      this.scene.add( this.gridHelper );
      this.axesHelper = new Three.AxesHelper( 5 );
      this.scene.add( this.axesHelper );
      container.appendChild(this.renderer.domElement);

    },
    animate: function() {
      requestAnimationFrame(this.animate);
      this.group.rotation.y +=.009;
      this.renderer.render(this.scene, this.camera);
    },
    onWindowResize: function () {
      this.renderer.setSize( window.innerWidth, window.innerHeight );
      this.camera.aspect = window.innerWidth / window.innerHeight;
      this.camera.updateProjectionMatrix();
    }
  },
  created() {
  window.addEventListener( 'resize', this.onWindowResize, false );
  },
  mounted() {
      this.init();
      this.animate();
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
 #container{
   height: 100vh;
 }
</style>
