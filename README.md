import React from 'react'
import { helloWorldService } from '../Services'

const   Springservice = () => {
  const handleClick = async () => {
    const serviceResponse = await helloWorldService();
    alert(serviceResponse);
  }
  return (
    <>
      <button onClick={handleClick}>
        Get
      </button>
    </>
  )
}

export default Springservice

---------------------


import axios from 'axios'

export var helloWorldService = async() => {
  let response;
  await axios.get('http://localhost:8080/process')
              .then(res => {
                console.log(res);
                response= res.data;
              })
              .catch(err => {
                console.log(err);
              }) 
          return response;
}
