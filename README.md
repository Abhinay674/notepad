async renderProducts() {
  const productCards = await Promise.all(this.state.allProductsDetails.map(async (prod, index) => {
    const imageUrl = await this.convertmodelToImage(prod.fullfilepath);
    return (
      <div className='card' key={index} onClick={() => this.cardClick(prod,index)} id={`myBtn3dViewer${index}`}>
        <img src={imageUrl} alt="fake-holder-img" className='card-image' height="200px" width="100%" />
        <div className='card-content'>
          <p>{prod.productCategory}</p>
          <p className='card-text-bold'>{prod.productname}</p>
        </div>
      </div>
    );
  }));

  return (
    <div className='cards'>
      {productCards}
    </div>
  );
}
