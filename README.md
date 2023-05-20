loaderGLTF.load(`${process.env.REACT_APP_VALIDATOR}/static/` + filename + "_" + this.state.templateTypeRadio + fileFormat, gltf => {
                    console.log('start of loader');
                    var object = gltf.scene;
                    console.log("object in loader", object)
                    object.rotation.y = 1.57;
                    object.updateMatrixWorld();
                    var box = new THREE.Box3().setFromObject(object);
                    var size = box.getSize().length();
                    var center = box.getCenter();
                    console.log('middle of loader');
                    object.position.x += (object.position.x - center.x);
                    object.position.y += (object.position.y - center.y);
                    object.position.z += (object.position.z - center.z);
                    this.controls.maxDistance = size * 1;
                    this.camera.position.copy(center);
                    this.camera.position.x += size / 2.7;
                    this.camera.position.y += size / 5.0;
                    this.camera.position.z += size / 0.80;
                    this.camera.near = size / 10;
                    this.camera.far = size * 100;
                    this.camera.updateProjectionMatrix();
                    this.camera.lookAt(center);
                    this.controls.update();
                    this.scene.add(object);
                    console.log('end of loader');
                    
                    
                    
                    
                    
                    Uncaught (in promise) TypeError: Cannot read properties of undefined (reading 'subVectors')
    at e.value (three.module.js:4172:58)
    at template-approval.js:249:36
    at GLTFLoader.js:189:6
    at GLTFLoader.js:2262:5
