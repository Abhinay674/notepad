import React, { Component } from 'react';

class MyComponent extends Component {
  state = {
    allproducts: [
      {
        fullfilepath: 'example.gltf',
        prodid: 1
      },
      {
        fullfilepath: 'another_example.gltf',
        prodid: 2
      }
    ]
  }

  Convert = (gltf) => {
    // Your implementation of the Convert function goes here
    // This function should return the data64 string
  }

  generateProductArray = () => {
    const { allproducts } = this.state;
    const productArray = [];

    allproducts.forEach((product) => {
      const { prodid, fullfilepath } = product;
      const data64 = this.Convert(fullfilepath);

      productArray.push({
        [prodid]: data64
      });
    });

    return productArray;
  }

  render() {
    const productArray = this.generateProductArray();

    // Your component rendering goes here

    return (
      <div>
        {productArray.map((product) => (
          <div key={Object.keys(product)[0]}>
            <p>{Object.keys(product)[0]}</p>
            <p>{Object.values(product)[0]}</p>
          </div>
        ))}
      </div>
    );
  }
}

export default MyComponent;
