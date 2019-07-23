# middleware
As name suggests middleware comes in middle of something and that is request and response cycle.
On the other word, it's just a function which gets executed on the incoming request.<br>
_Authorization middleware should look like as below,_

``` javascript
const jwt = require('jsonwebtoken');

module.exports = (req,res,next)=>{
    try{
    const token = req.headers.authorization.split("")[1];
    jwt.verify(token,'secret_key');
    next();
    }catch(error){
    res.status(401).json({message:'Auth Failed!'});
    }
}
```
