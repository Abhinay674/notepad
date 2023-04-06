<div className="cards">
                        { this.state.allProductsDetails.map(async (prod, index) => {
                            const imageUrl = await this.convertmodelToImage(prod.fullfilepath); 
                            console.log('ImageURL'+ imageUrl);
                            return (<>                                
                                <div className="card" key={index} onClick={() => this.cardClick(prod, index)} id={`myBtn3dViewer${index}`}>  
                                    <img src={imageUrl} alt="fake-holder-img"  className="card-image" height="200px" width="100%" />
                                     {/* <img src={`product/image${index}.PNG`} alt='fake-holder-img' className="card-image" height="200px" width="100%" /> */}
                                    <div className="card-content">
                                        <p>{prod.productCategory}</p>
                                        <p className="card-text-bold">{prod.productname}</p>
                                    </div>
                                </div>

                            </>)
                            })
                        }
