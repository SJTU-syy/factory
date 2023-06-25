<template>
  <div>
    <p>搭建基础流程</p>
    <div id="webgl" style="margin-top: 200px;margin-left: 100px;"></div>
  </div>
</template>

<script>
import * as THREE from 'three'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls'

export default {
name: 'ThreeTest',
data() {
  return {
    scene: null,
    camera: null,
    renderer: null,
  }
},
methods: {
  init(){
// 创建3D场景对象Scene
this.scene = new THREE.Scene();


const width = 800; //宽度
const height = 500; //高度
// 30:视场角度, width / height:Canvas画布宽高比, 1:近裁截面, 3000：远裁截面
this.camera = new THREE.PerspectiveCamera(30, width / height, 1, 3000);
//相机在Three.js三维坐标系中的位置
// 根据需要设置相机位置具体值
this.camera.position.set(200, 200, 200); 
//相机观察目标指向Threejs 3D空间中某个位置
this.camera.lookAt(0, 0, 0); //坐标原点


// 创建渲染器对象
this.renderer = new THREE.WebGLRenderer();
// 定义threejs输出画布的尺寸(单位:像素px)
const canvas_width = 800; //宽度
const canvas_height = 500; //高度
this.renderer.setSize(canvas_width, canvas_height); //设置three.js渲染区域的尺寸(像素px)
document.getElementById('webgl').appendChild(this.renderer.domElement);


//创建orbit
const controls = new OrbitControls(this.camera, this.renderer.domElement);

},

  model(){
//创建一个长方体几何对象Geometry
const geometry = new THREE.BoxGeometry(100, 100, 100);

//创建一个材质对象Material
const material = new THREE.MeshBasicMaterial({
    color: 0xff0000,//0xff0000设置材质颜色为红色
}); 

// 两个参数分别为几何体geometry、材质material
const mesh = new THREE.Mesh(geometry, material); //网格模型对象Mesh
mesh.position.set(0,10,0);

//添加物体
this.scene.add(mesh); 
},

  render() {

    this.renderer.render(this.scene, this.camera); //执行渲染操作
    requestAnimationFrame(this.render);//请求再次执行渲染函数render，渲染下一帧
    
  }
},
mounted() {
    this.init();
    this.model();
    this.render()
}
}
</script>
<style scoped>
#container {
  height: 400px;
}
</style>