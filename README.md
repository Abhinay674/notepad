import React,{useState,useEffect,useRef} from 'react';
import * as THREE from 'three';
import html2canvas from 'html2canvas';
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader.js';



function ThreeToJpeg({modelUrl}) {
    const [imageUrl,setImageUrl] = useState(null);
    const canvasRef = useRef(null);

    useEffect(() => {
       const loader = new GLTFLoader();
       loader.load('/assets/Mohith.gltf',(gltf) => {
        const scene = gltf.scene;
        const camera = new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,0.1,1000);
        camera.position.z = 5;
        const canvas = document.createElement('canvas');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        const renderer = new THREE.WebGLRenderer({ canvas });
        renderer.render(scene,camera);

        html2canvas(canvas,{ foreignObjectRendering: true, canvas: canvasRef.current }).then((canvas) => {
            const dataUrl = canvas.toDataURL('image/jpeg');
            setImageUrl(dataUrl);
        })
       })
    },[]);


    return (
        <div>
            <canvas ref={canvasRef} width={1024} height={1024} style={{display: 'none'}} /> 
             {imageUrl && <img src={imageUrl} alt="3D Model" />}
        </div>
    )


}

export default ThreeToJpeg
