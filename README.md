import React,{useState,useEffect,useRef} from 'react';
import * as THREE from 'three';
import html2canvas from 'html2canvas';
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader';



function ThreeToJpeg() {
    const [imageUrl,setImageUrl] = useState(null);
    const canvasRef = useRef(null);

    useEffect(() => {
       const loader = new GLTFLoader();
       loader.load(`/assets/Mohith.gltf`,(gltf) => {
        const scene = gltf.scene;
        const camera = new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,0.1,1000);
        camera.position.z = 5;

        const canvas = document.createElement('canvas');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const renderer = new THREE.WebGLRenderer({ canvas });
        renderer.render(scene,camera);

        setTimeout(() => {
            html2canvas(canvasRef.current,{allowTaint: true}).then((canvas) => {
                const dataUrl = canvas.toDataURL('image/jpeg');
                setImageUrl(dataUrl);
            })
        },0);
    })
    },[]);


    return (
        <div>
            <canvas ref={canvasRef} width={1024} height={1024} /> 
             {imageUrl && <img src={imageUrl} alt="3D Model" />}
        </div>
    )


}

export default ThreeToJpeg






loader.load(
      'model.gltf',
      (gltf) => {
        const canvas = canvasRef.current;
        const renderer = new CanvasRenderer({ canvas });

        renderer.render(gltf.scene, gltf.camera);

        const dataURL = canvas.toDataURL('image/jpeg');
        setJpgImageData(dataURL);
      },
      (error) => {
        console.log('Error loading GLTF file:', error);
      }
    );
  }, []);

  if (!jpgImageData) {
    return <div>Loading...</div>;
  }

  return (
    <div>
      <img src={jpgImageData} alt="JPG Image" />
      <canvas ref={canvasRef} style={{ display: 'none' }} />
    </div>
  );
};

export default GltfToJpg;

