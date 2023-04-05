{ this.state.allProductsDetails.map(async (prod, index) => {                   
                            if(prod.productid === 86){
                                console.log(prod.productid);        
                                const imageUrl = await convertmodelToImage(prod.fullfilepath);       
                                console.log('return imagurl ' + imageUrl);  
                     
                                 return (
                                    <>
                                        <div className='card' key={index} onClick={() => this.cardClick(prod,index)} id={`myBtn3dViewer${index}`}>
                                            <img src={imageUrl} alt="fake-holder-img" className='card-image' height="200px" width="100%" />
                                            <div className='card-content'>
                                                <p>{prod.productCategory}</p>
                                                <p className='card-text-bold'>{prod.productname}</p>
                                            </div>
                                        </div>  
                                    </>
                                )
                            }       
