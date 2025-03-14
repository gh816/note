# three

- **Scene**：场景是 Three.js 中所有对象的容器，包括模型、灯光、相机等。
- **Camera**：相机决定了场景的视角，常用的有透视相机（PerspectiveCamera）和正交相机（OrthographicCamera）。
- **Renderer**：渲染器负责将场景和相机的内容渲染到画布上。
- **Geometry**：定义物体的形状（如立方体、球体）。
- **Material**：定义物体的外观（如颜色、纹理）。
- **Mesh**：几何体和材质的组合，是场景中可渲染的对象。

### **性能优化**

创建一个3D汽车模型案例步骤，

1.首先创建一个场景scene = new THREE.Scene();

2.创建相机

这个是模拟人眼视角

camera = new THREE.PerspectiveCamera(75, width / height, 0.1, 1000);

创建相机有4个参数

参数1：视野角度，单位是度。它决定了相机能够看到的范围。值越大，看到的范围越广。

参数2：宽高比，通常是画布的宽度除以高度。它确保渲染的画面不会变形。

参数3：近裁剪面。距离相机小于这个值的物体不会被渲染。

参数 4：远裁剪面。距离相机大于这个值的物体不会被渲染。

3.创建渲染器

renderer = new THREE.WebGLRenderer({ antialias: true });

渲染器的作用是把 3D 场景（`THREE.Scene`）和相机（`THREE.Camera`）的内容渲染到网页的画布（`<canvas>`）上。

4.添加轨道控制器

controls = new OrbitControls(camera, renderer.domElement);

轨道控制器是一种常用的交互工具，允许用户通过鼠标或触摸屏控制相机的位置和视角，从而实现场景的旋转、缩放和平移。

5.*添加光源*

const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);

const directionalLight = new THREE.DirectionalLight(0xffffff, 0.8);

6.加载贴图

立方体贴图通常用于模拟环境反射

 const cubeMap = new THREE.CubeTextureLoader().load(envUrls);  这个是加载立方体贴图

 cubeMap.format = THREE.RGBAFormat;  设置立方体贴图的像素格式为 `RGBAFormat`

 cubeMap.mapping = THREE.CubeReflectionMapping;  设置立方体贴图的映射方式为 `CubeReflectionMapping`