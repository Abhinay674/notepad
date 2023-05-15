if(incomingFile) {
            let object = incomingFile.name;
            console.log(object);
            let value= await ModelToImage(`http://10.245.74.14:3004/static/${object}`);
            // let value= await ModelToImage(`/opt/ixrvp/Storage/3DAssets/${object}`);
            console.log('value' + value);
            let base64_imageLink1 = String(value).split(',')[1];
            console.log(base64_imageLink1);
            let imageStr = `data:image/jpeg;base64,${base64_imageLink1}`;
    let name = incomingFile.name.split('.')[0]+'.jpeg';
    console.log('name:',name);
    async function UrltoFile(){
            const file = await  urltoFile(imageStr, name ,'image/jpeg');
            console.log('JPG FILE::'+ file);
            const data = new FormData();
            data.append('file',file);
            console.log('form data'+ data);
            await axios.post(`${process.env.REACT_APP_UPLOAD_DOWNLOAD_FILE}/file-api/all-info/addfile`, data)
            .then(res => {
                console.log(res);
            })
            .catch(error => {
                console.log(error)
            })
        }
        UrltoFile();
    }
