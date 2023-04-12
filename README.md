let fileName;

        urltoFile(imageStr, 'Model.jpg','image/jpeg')
            .then((file) => { console.log(file.name);} );

            console.log('filename::' + fileName);
