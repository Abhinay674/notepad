import React from 'react';
import '../styles/dashboard.css';
import { Link } from 'react-router-dom';
import { getProjects, getCatalogues, deleteCatalogues } from '../Services';
import Catalogue_all from '../components/catalogue_all';
import { props } from 'bluebird';


class Dashboard extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            AllProjects: null,            
            // BulkUploaded: [],
        }
    }


    componentDidMount = async () => {
        // var Projects= await getProjects();
        // console.log('Projects',Projects);
        // this.setState({
        //     AllProjects: Projects
        // })

        //Get all the catalogues from backend to show as a cards
        let allCatalogues = await getCatalogues();
        this.setState({
            AllProjects : allCatalogues
        })
        console.log(allCatalogues);
        console.log('All products',this.state.AllProjects);
    }  

    //   deleteFunction = async (id) => {
    //     console.log('id',id);
    //     if(window.confirm('Are you sure you want to delete this catalogue?')){
    //         this.setState({
    //             AllProjects: this.state.AllProjects.filter((item) => item.catlogueId !== id)
    //         })
    //     }        
    //     var response = await deleteCatalogues(id);
    //     console.log("Catalogue successfully deleted with"+id);
    //     alert(response);
    //     }


        handleAdd = (obj) => {
                console.log('handleAdd',obj);
                // const newObj = this.state.AllProjects.map(prod => {
                //     console.log('Inside handleAdd');
                //     if(prod.catlogueId === obj.catlogueId){
                //         return obj;
                //     }
    
                //     return prod;
                // });
                
                // this.setState({
                //     AllProjects : newObj
                // })
            console.log('end of handleAdd');
        }


    render() {
        return (
            <div className="dashboard-container">
                <div className="user-greeting" style={{ display: "inline" }}>
                    <h2>Welcome Back, User!</h2>                    
                    <h3>Let's look at your Catalogue</h3>
                </div>
                <div className="dashboard-grid">
                    {
                        this.state.AllProjects ?
                            this.state.AllProjects.filter((item) => item.catlogueId > 54).map((project, index) => {
                                return (
                                    <div className="dashboard-card" key={index}>
                                        <div className="text">
                                            <h5 className="client">Blue Text</h5>
                                            {/* <p className="catalogue">{project.catalogueName}&emsp;&nbsp;<button onClick={() => this.deleteFunction(project.catlogueId)}>Delete</button> */}
                                            <p className="catalogue">
                                                 {project.catalogueName}
                                                <progress id="file" value="32" max="100"> 32% </progress>
                                            </p>
                                            <p className="dashboard-card-info">Men 162 Products, Women 86 Products Filter By Fit, Style, Wash, Color and Size Sort By Most popular</p>
                                        </div>
                                        <hr id="hr" />
                                        {/* <Link className="hiddenLinks" to="">Edit</Link> &emsp; */}
                                        {/* <Link className="hiddenLinks" to={{pathname:"/edit_products",state:{prods: project.productsList}}}>Edit</Link>&emsp;&nbsp; */}
                                        <Link className="hiddenLinks" to={{pathname:"/edit_products",state:{prods:project,addProduct:this.handleAdd()}}}>Edit</Link>&emsp;&nbsp;
                                        {/* <Link className="hiddenLinks" to={{pathname:"/edit_products"}}>Edit</Link>&emsp;&nbsp; */}
                                        <Link className="hiddenLinks" to={{pathname:"/createstore_custom", state:{prods: project}}}>Create Store</Link>&emsp;&nbsp;
                                        <Link className="hiddenLinks" to={{pathname:"/createstore_upload", state:{prods: project}}}>Empty Store</Link>&emsp;&nbsp;
                                        <Link className="hiddenLinks" to='/visualize_store'>Room Planner</Link>
                                    </div>
                                )
                            }) : console.log("No projects")
                    }
                </div>
            </div>
        )
    }
}
export default Dashboard;





import React, { useState, useEffect } from "react";
import "../styles/catalogue_create-catalogue.css";
import { getAllProducts } from "../Services";
import Spinner from "./Spinner";
import { useLocation } from "react-router-dom";


function UpdateCatalogue(props) {

    const [allProductsDetails, setAllProductDetails] = useState([]);
    const [newState,setNewState] = useState({});



    const location = useLocation();
    const products = location.state.prods;
    console.log('products',products);
    const handleAdd = location.state.addProduct;


    
    const [loading, setLoading] = useState(true);
    
    const [items, setItems] = useState(products);

    useEffect(async () => {
        setAllProductDetails(await getAllProducts());
        setLoading(false);
    });

    console.log('products',allProductsDetails);
    
    var collectSelected = (product) => {
        console.log("checkbox", product);
        const obj = {...product};
        console.log('obj',obj);
        setNewState(obj);
    };
    console.log('newobject',newState);



    
    var getElements = () => {
        console.log('newstate',newState);
        const obj = {
            ...items,
            productsList:[...items.productsList,newState]
        }

        console.log('add item',obj)
        setItems(obj);

        handleAdd('hello');
        console.log('getelements',items);
        alert('Catalogue Updated !')
        
    }
 

console.log('items',items);


    //==========================================================================//
    return loading ? (
        <Spinner />
    ) : (
        <div>
            <p className="createCatalogueHead">Select the items to update your catalogue</p>
            <div className="cards">
                {allProductsDetails.filter(prod => prod.productid > 171).map((prod, index) => {
                    var filename;
                    var file = prod.filename;
                    if(file !== null){
                        var fileArray = file.split('.');
                        filename = fileArray[0];    
                    } 

                   return (
                    <>
                        <div className="card" key={index} id={`myBtn3dViewer${index}`}>
                         {/* <img src={`product/image${index}.PNG`}  */}
                         <img src={`http://localhost:3004/static/${filename +'.jpeg'}`}
                             className="card-image" height="200px" width="100%" 
                                alt='fake-holder-img'
                                />
                            <div className="card-content">
                                <p>{prod.productCategory}</p>
                                <p className="card-text-bold">{prod.productname}</p>
                            </div>
                            <input
                                type="checkbox"
                                id="checkCheck"
                                className="createCatalogueCheck"
                                checked={ items.productsList.find(item => item.productid === prod.productid) }
                                // checked={()=> collectSelected(prod.productname)}  
                                onChange={() => collectSelected(prod)}
                                value={prod.productname}></input>
                        </div>
                    </>
                ) } )
                }
                </div>
            <button
                className="createCatalogueButton"
                onClick={() => getElements()}
            >Update Catalogue</button>
            
            
            
        
        </div>
    );
}
export default UpdateCatalogue;






