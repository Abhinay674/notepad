const buffer = Buffer.from(imageStr, 'base64');
        const formData = new FormData();
        formData.append("myFile", buffer, { filename: 'Model.jpg' });
        console.log(formData); 
 
 
 Failed to execute 'append' on 'FormData': parameter 2 is not of type 'Blob'.
    at FileDump (function.js:52:1)
