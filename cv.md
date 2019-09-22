# CV 2019

## Personal information
![Personal photo](http://bykovsky.dev/img/2017_005650.png)

**Name:** Gleb Bykovsky 
**Address:** Belarus, Gomel 
**Email:** gleb@sgsrv.ru  
**Phone:** +3752-5678-5432 

## About me
I started learning to code at 24 years. I've learned Pascal, Java and Php in university. My diploma project had been writen with php, it was a flower shop project for costumer from Russia. After university i was working as a system administrator for about 2 years. But this work didn't get me enough pleasure, it was interesting when i was writting different shell scrypts and was busy with other work related with programming only. Meanwhile I started learning MEAN stack, i wrote some simple application after it and got one important thing - programming is really interesting and cool thing, and i really wanna dedicate myself for it.
Now, i've been working as a fullstack developer, but i know exactly - i don't have enough knowledges and good skill, i have to get it and work at serious IT company such as EPAM for example, that's why i have to finish these courses :)

## Code example
```
static async regUser(ctx) { 
    const params = ctx.request.body;
    try{
        const searchUser = await knex('users').where('email',params.email);
        if(searchUser.length == 0){
            const salt = crypto.randomBytes(16).toString('hex');
            const result = await knex('users').returning('id').insert([
                {
                    name: params.name,
                    email: params.email,
                    note: params.note,
                    salt: salt,
                    hash: crypto.pbkdf2Sync(params.password, salt, 1000, 64, 'sha512').toString('hex')
                }
            ]);
            const payload = { 
                subject: result.join() 
            }
            const token = jwt.sign({
                payload, 
                exp: Math.floor(Date.now() / 1000) + (60 * 60 * 24)
            },"secretKey"
            ); 
            ctx.body = {
                token: token
            }           
        }else{
            ctx.throw(409, 'User with such email already exists!');
        }
    } catch(error){
        wlogger.log('error', 'code/models/regUser() => ' + error.message)
        ctx.throw(500,error);
    }       
} 
```

## Education
| University                              | Faculty                             | Specialty   |
|-----------------------------------------|-------------------------------------|-------------|
| Francisk Skorina Gomel State University | Faculty of Information technologies | IT Engineer |

## Skills
 - HTML, CSS/SCSS;
 - JavaScript. Have experience with: Node, Express, Koa, Knex, Mongoose, Objection, Angular(6,7,8);
 - Databases (MySQL, PostgreSQL, MongoDB, MsSQL);
 - PHP(5.3, 7.0), Java(SE), PowerShell.

## Languages
 1. Russian — native.
 1. English — B1.

### Gomel, 2019, Bykovsky Gleb