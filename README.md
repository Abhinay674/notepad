const products = [
  { fullfilepath: 'path/to/file1.gltf', prodid: 1 },
  { fullfilepath: 'path/to/file2.gltf', prodid: 2 },
  { fullfilepath: 'path/to/file3.gltf', prodid: 3 }
];

async function convertToImageUrl(fullfilepath) {
  // Function to convert fullfilepath to image url
  // Returns a promise that resolves to the image url string
  // Example usage: await convertToImageUrl(products[0].fullfilepath)
}

async function generateProductArray() {
  const productArray = await Promise.all(products.map(async (product) => {
    const imageUrl = await convertToImageUrl(product.fullfilepath);
    return [product.prodid, imageUrl];
  }));
  return productArray;
}

// Example usage
generateProductArray().then((productArray) => {
  console.log(productArray);
});
