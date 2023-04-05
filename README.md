import React, { useState, useEffect } from 'react';
import ModelToImage from './ModelToImage';
import Base64Image from './Base64Image';

const ImageRender = () => {
  const [base64String, setBase64String] = useState(null);

  useEffect(() => {
    async function fetchImage() {
      let imageLink = await ModelToImage('../colorway_BQ7270.glb');
      let base64String = imageLink['[[PromiseResult]]']; // extract the base64 string from the resolved promise
      setBase64String(base64String); // update the state with the base64 string
    }

    fetchImage();
  }, []); // run the effect only once, on mount

  return (
    <div>
      {base64String ? (
        <Base64Image b64String={base64String} />
      ) : (
        <p>Loading...</p>
      )}
    </div>
  );
};

export default ImageRender;
