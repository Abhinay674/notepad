 const link = document.createElement('a');
        link.download = 'Model.png';
        link.href = renderer.domElement.toDataURL('image/png').replace('image/png', 'image/octet-stream');
        container.innerHTML = ""
        resolve(link.href)
        link.click();
        console.log('link.href: ' + link.href)
        return link.href
