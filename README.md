 async function UrltoFile(){
            const file = await  urltoFile(imageStr, name ,'image/jpeg');
            console.log(file);
            await axios.post(`${process.env.REACT_APP_UPLOAD_DOWNLOAD_FILE}/file-api/all-info/addfile`, file)
                .then(res => {
                    console.log(res);
                })
                .catch(error => {
                    console.log(error)
                })
        }
        UrltoFile();
