ERROR in ./src/components/function.js 9:4-21
Module not found: Error: Can't resolve 'buffer' in 'C:\Users\abhinay.kumar04\jpg-upload\src\components'

BREAKING CHANGE: webpack < 5 used to include polyfills for node.js core modules by default.
This is no longer the case. Verify if you need this module and configure a polyfill for it.

If you want to include a polyfill, you need to:
        - add a fallback 'resolve.fallback: { "buffer": require.resolve("buffer/") }'
        - install 'buffer'
If you don't want to include a polyfill, you can use an empty module like this:
        resolve.fallback: { "buffer": false }
