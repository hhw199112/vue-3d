<template>
    <div id="webgl"></div>
</template>
<script>
import * as THREE from 'three'
export default{
    methods:{
         Init(){
            const scene=new THREE.Scene();
            const geometry=new THREE.BoxGeometry(100,60,20);
            const material=new THREE.MeshBasicMaterial({
                color:0x0000ff,
                transparent:true,
                opacity:0.5
            });
            const mesh=new THREE.Mesh(geometry,material);
            mesh.position.set(100,0,0);
            scene.add(mesh);

            const camera=new THREE.PerspectiveCamera();
            camera.position.set(-1000,0,0);
            camera.lookAt(-2000,0,0);
            //camera.lookAt(0,50,0);

            const axesHelper=new THREE.AxesHelper(50);
            scene.add(axesHelper);


            const renderer=new THREE.WebGLRenderer();
            const width=window.innerWidth;
            const height=window.innerHeight;
            renderer.setSize(width,height);
            renderer.render(scene,camera);
            document.getElementById('webgl').appendChild(renderer.domElement);

        }
    },
    mounted(){
       this.Init();
    }
}
</script>
<style scoped>
#webgl{
    overflow-y:hidden;
    overflow-x: hidden;
}
</style>
