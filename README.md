const link = document.createElement('a');
        // let fileName = modelUrl.split('.')[0];
        link.download = 'Model.jpg';
        console.log(link);
        link.href = renderer.domElement.toDataURL('image/jpeg').replace('image/jpeg', 'image/octet-stream');
        container.innerHTML = ""
        resolve(link.href);
        link.click();

        const blob = new Blob([renderer.domElement.toDataURL('image/jpeg').split(',')[1]],
        saveAs(blob,'D:\ModeltoJpg\Model.jpg')
        )
        // console.log('link.href: ' + link.href)
        return link.href;
