import axios from 'axios';

export var fileExist = async (fileName) => {
    var statusArray = [];
    var status = null;
    await axios.get(`${process.env.REACT_APP_VALIDATOR}/static/` + fileName + '.glb')
        .then(resp => {
            console.log("response", resp)
            if (resp.status === 200) {
                status = true;
                statusArray.push(fileName + '.glb');
            } else {
                status = false;
                statusArray.push(fileName + '.glb');
            }
        })
        .catch(err => {
            console.log(err);
        })

    if (!status) {
        await axios.get(`${process.env.REACT_APP_VALIDATOR}/static/` + fileName + '.gltf')
            .then(resp => {
                console.log("response", resp)
                if (resp.status === 200) {
                    status = true;
                    statusArray.push(fileName + '.gltf');
                } else {
                    status = false;
                    statusArray.push(fileName + '.gltf');
                }
            })
            .catch(err => {
                console.log(err);
            })
    } 

    return statusArray;
}











// export var fileExist = async (fileName) => {
//     console.log("fileName in Validator", fileName)
//     var statusArray = [];
//     var status = null;
//     var fileFormat = null;
//     await axios.get(`${process.env.REACT_APP_VALIDATOR}/static/` + fileName + '.glb')
//         .then(resp => {
//             // console.log("response", resp)
//             if (resp.status === 200) {
//                 status = true;
//                 fileFormat = ".glb"
//                 statusArray.push(status, fileFormat)
//             } else {
//                 status = false;
//                 statusArray.push(status, fileFormat)
//             }
//         })
//         .catch(err => {
//             status = false;
//             statusArray.push(status, fileFormat)
//         })

//     if (!status) {
//         await axios.get(`${process.env.REACT_APP_VALIDATOR}/static/` + fileName + '.gltf')
//             .then(resp => {
//                 // console.log("response", resp)
//                 if (resp.status === 200) {
//                     status = true;
//                     fileFormat = ".gltf"
//                     statusArray.push(status, fileFormat)
//                 } else {
//                     status = false;
//                     statusArray.push(status, fileFormat)
//                 }
//             })
//             .catch(err => {
//                 status = false;
//                 statusArray.push(status, fileFormat)
//             })
//     } else {
//         statusArray.push(status, fileFormat)
//     }


//     return statusArray;
// }









import React, { useState, useEffect } from 'react';
import ModelToImage from './ModelToImage';
import {fileExist} from '../services';

const ImageRender = () => {
  const [imageDisplay,setimageDisplay] = useState(false);
  const [imageUrl,setImageUrl] = useState(null);
  const [gltf,setGltf] = useState([]);

  
useEffect(() => {
        async function fetchImage() {

            await fileExist('ShirtY').then(async (resp) => {
                  console.log(resp);
                  setGltf(resp)
                  let imageLink = await ModelToImage(gltf[0]);
                  console.log('Await imageLink:'+ imageLink);
                  let value = imageLink;
                  let base64_imageLink1 = String(value).split(',')[1];
                  console.log(base64_imageLink1);
                  let imageStr = `data:image/jpeg;base64,${base64_imageLink1}`;
                  setImageUrl(imageStr)
                  console.log(imageStr);
                  setimageDisplay(true);

            }).catch((err) => console.log(err));

	      }

	fetchImage()
},[]);


  return (
      <div>
      {imageDisplay? 
           <img src={imageUrl} />  : null } 
       </div>
    )
    
};

export default ImageRender;

