HEROKU: Plataforma que esta orientada a proveer servidores de todo tipo de lenguajes. Entrega todo listo para que se ponga la aplicación ahi y la devuelva funcionando.

Instalar Heroku para Windows 64
instalar Heroku en cmder  //  npm i -g heroku

Proyecto

1) Registrarte en heroku // keroku login
heroku: Press any key to open up the browser to login or q to exit: // Le doy enter para logearme
Opening browser to https://cli-auth.heroku.com/auth/cli/browser/0a4778ef-5634-4a06-8309-931d7da42bb0?requestor=SFMyNTY.g2gDbQAAAA0xODEuMTAuMjM3LjIybgYAuDC8RH4BYgABUYA.ifkfg8KwH2xg0fLU0fd1WXKNU5Cxmo-y2ILIUWPjGCk
heroku: Waiting for login... /     // Me redirecciona a la url de heroku

2) Crear un proyecto de Heroku (Se crea el servidor) con su respectiva aplicacion // heroku create
Creating app... done, ⬢ calm-basin-98431
https://calm-basin-98431.herokuapp.com/ | https://git.heroku.com/calm-basin-98431.git
Ademas, se agrego un git. Se comprueba con git remote -v  // Crea un origin en el repositorio de git
    heroku  https://git.heroku.com/calm-basin-98431.git (fetch)
    heroku  https://git.heroku.com/calm-basin-98431.git (push)

3) Comprobar que funcione correctamente  // node index.js  //  Server running on http://localhost:3001

4) Levantar el servidor  //  git push heroku master  // master: nombre de la rama
    Envia un push al servidor de git (se sube todo ese codigo al servidor)

5) Verifico en heroku url  //  https://dashboard.heroku.com/apps  //  Se observa que se ejecuto el Buil y Deployed.

6) Abrir la aplicación y verla en heroku url  //  Open app  // Saltará un error
    Aclaración (3001): No se le puede asignar el puerto a mi aplicación cuando lo voy a desplegar a producción, porque el puerto lo asigna dinamicamente heroku ya que tiene un puerto especial para cada aplicación (No va a abrir siempre el 3001, el 8080, etc.), es decir que va a abrir un puerto de acuerdo a la disponibilidad que haya

7) Agarrar el puerto de una variable de entorno (index.js de la carpeta notes)  //  process.env.PORT || 3001
    Aclaración: Del proceso agarre la variable de entorno PORT, o agarre el puerto 3001 

8) git add .  //  git commit -am ""  //  git push heroku master  //  Item 5 nuevamente

Verificar que corra la App en Heroku

1) Crear una nuevo repositorio en Git con el index.js a ejecutar. Siempre desde el cmder, llevar los cambios al repositorio 
                                    // git add . // git commit -am "" // git push
2) Una vez ya dentro de Heroku, crear una una app // Create a new app
3) Conectar con GitHub
4) Escoger el repositorio creado.
5) Clickear en Enable Automatic Deploys
6) Dentro de Overview, verificar "Build succeeded" y "Deployed"
7) Open app. Desarrollo efectuado correctamente: Aplicación desplegadada en producción.


RESOLVER CORS DE NODEJS
CORS es un paquete de node.js para proporcionar un middleware Connect / Express que se puede usar para habilitar CORS con varias opciones.

1) En cmder instalar la libreria que usaremos en express // npm i cors
2) Requerir cors. En archivo index.js// const cors = require('cors')
3) Usar cors. En index.js // app.use(cors())
    Aclaración: La sintaxis usada la determino de la documentación del paquete cors
4) add. // git commit -am "" // git push // a repositorio GitHub (O Heroku) para actualizar contenido (git remote -v para visualizar repositorios)
5) Ahora si se puede acceder a los datos a traves de github
6) Verificación en consola de url

(async () => {
    const response = await fetch('https://app-personaldemofede.herokuapp.com/')
    const users = await response.json()
    console.log(users)
})()



ARQUITECTURA Y MODURALIZACIÓN DE CODIGOS

Se utiliza express.Router para crear manejadores de rutas montables y modulares. Una instancia Router es un sistema de middleware y direccionamiento completo; 
por este motivo, a menudo se conoce como una “miniaplicación”.

1) Dejar de usar un archivo index para todo
2) Crear item particulares de acuerdo a necesidades especificas (por ejemplo personas, cantidades, etc.)
3) Crear en la raiz, un archivo unico de todas las rutas (routes.js)
4) Se importa el archivo de rutas al index.js del item en particular particular
5) Pasarle la app al item en particular, el cual previamente habia sido llamado por express
6) Ver carpeta FEDERICO (MASTER-HEROKU)
 