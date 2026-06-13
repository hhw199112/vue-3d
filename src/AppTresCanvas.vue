<template>
  <div>
    <div id="webgl" class="centerCenterBottom"></div>
  </div>
</template>
 
<script setup>
import { onMounted } from 'vue'
import * as THREE from 'three'
 
 
function init() {
 //  场景
 let scene = new THREE.Scene();
 
 // 摄像机
 // // 45:视场角度, width / height:Canvas画布宽高比, 1:近裁截面, 3000：远裁截面
 let camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 1, 3000);
 // 相机位置
 camera.position.x = -10;
 camera.position.y = 30;
 camera.position.z = 30
 //相机观察目标指向Threejs 3D空间中某个位置
 camera.lookAt(scene.position);


 // 渲染器
 let renderer = new THREE.WebGLRenderer();
 //设置three.js渲染区域的尺寸(像素px)
 renderer.setSize(window.innerWidth, window.innerHeight);
 // document.body.appendChild(renderer.domElement);
 //画布要插入到的HTML元素
 document.getElementById('webgl').appendChild(renderer.domElement);

 // 设置渲染器渲染阴影效果
 renderer.setClearColor(new THREE.Color(0x000000));
 // 渲染器允许阴影渲染
 renderer.shadowMap.enabled = true;

 // 坐标轴
 //hree.js坐标轴
 let axes = new THREE.AxesHelper(20);
 scene.add(axes);


 // 平面
 //创建了一个长和宽分别为 60 和 20,高为 1,宽度的方向的边框为 1 的平面对象
 let planeGeometry = new THREE.PlaneGeometry(60, 20, 1, 1);
 //材质对象
 let planeMaterial = new THREE.MeshLambertMaterial({ color: 0xcccccc });
 let plane = new THREE.Mesh(planeGeometry, planeMaterial);
 plane.rotation.x = -0.5 * Math.PI;
 plane.position.x = 30
 plane.position.y = 0
 plane.position.z = 0
 scene.add(plane);

 // 设置投影
 plane.receiveShadow = true;


 // 物体
 // 物体大小
 let geometry = new THREE.BoxGeometry(4, 4, 4);
 let material = new THREE.MeshLambertMaterial({ color: 0x00ff00 });
 let cube = new THREE.Mesh(geometry, material);
 //坐标
 cube.position.x = 10;
 cube.position.y = 2;
 cube.position.z = 0;

 // 设置投影
 cube.castShadow = true;
 scene.add(cube);


 // 光源
 let spotLight = new THREE.SpotLight(0xffffff);
 //光线是否随距离衰减
 spotLight.decay = 0.0;
 //坐标
 spotLight.position.set(0, 60, 5);
 scene.add(spotLight);

 // 设置投影
 spotLight.castShadow = true;

 renderer.render(scene, camera);
  
}
 
 
onMounted(
  () => {
    init()
  }
)
 
</script>
<style>
body {
  margin: 0;
}
 
canvas {
  width: 100%;
  height: 100%;
}
</style>