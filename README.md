import axios from 'axios';

export var fileExist = async (fileName) => {
    var gltf = '';
    await axios.get(`${process.env.REACT_APP_VALIDATOR}/static/` + fileName)
        .then(resp => {
            console.log("response", resp)
            gltf = fileName;
        })
        .catch(err => {
            console.log(err);
        })

    console.log(gltf);
    return gltf;
}


