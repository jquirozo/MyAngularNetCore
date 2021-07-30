# MyAngularNetCore
## VS 2022 con Angular + NetCore 

### El siguiente proceso genera el código inicial del proyecto, usando el IDE Visual Studio 2022 Preview, sin necesidad de realizar configuraciones complicadas. 

Pasos para tener la app ejecutando:
- [x] Crear en VS2022 un nuevo proyecto, usar la plantilla: **ASP.NET Core with Angular**
- [x] Abrir **appsettings.json** y asegurarse que la cadena de conexión *DefaultConnection* es correcta (si no existe la DB, el proyecto la generará con el siguiente paso)
- [x] Abrir el **Package Manager Console**, y generar/actualizar la DB: 
  > PM> Update-Database
  
  b) otra alternativa es ejecutar desde linea de comandos y en la ubicación del proyecto el comando:
    > dotnet ef database update

Al efecutar la solución (F5) se compilará el proyecto, el Back(NetCore) creará un proxy en https://localhost:5001 para despues exponer el Front(Angular) en https://localhost:5002/ 

- [x] Se pedirá instalar un certificado de confianza (debido al SSL que se configuró inicialmente en el proyecto), sólo acepte y genere el certificado al ejecutar el proyecto la primera ocasión(sólo para ambiente DEV, en PROD deberá instalar un certificado adecuado).

A continuación la ejecución inicial desde la consola del proyecto:
```
> myangularnetcore@0.0.0 prestart C:\code\MyAngularNetCore\ClientApp
> node aspnetcore-https

A valid HTTPS certificate is already present.

> myangularnetcore@0.0.0 start C:\code\MyAngularNetCore\ClientApp
> run-script-os

> myangularnetcore@0.0.0 start:windows C:\code\MyAngularNetCore\ClientApp
> ng serve --port 5002 --ssl --ssl-cert %APPDATA%\ASP.NET\https\%npm_package_name%.pem --ssl-key %APPDATA%\ASP.NET\https\%npm_package_name%.key

[HPM] Proxy created: [
  '/weatherforecast',
  '/_configuration',
  '/.well-known',
  '/Identity',
  '/connect',
  '/ApplyDatabaseMigrations'
]  ->  https://localhost:5001
Compiling @angular/core : es2015 as esm2015
Compiling @angular/common : es2015 as esm2015
Compiling @angular/platform-browser : es2015 as esm2015
Compiling @angular/forms : es2015 as esm2015
Compiling @angular/platform-browser-dynamic : es2015 as esm2015
Compiling @angular/common/http : es2015 as esm2015
Compiling @angular/router : es2015 as esm2015

|Initial Chunk Files   | Names         |      Size|

|vendor.js             | vendor        |   3.05 MB|
|styles.css, styles.js | styles        | 524.88 kB|
|polyfills.js          | polyfills     | 508.83 kB|
|main.js               | main          |  86.16 kB|
|runtime.js            | runtime       |   6.59 kB|

|                      | Initial Total |   4.15 MB|

Build at: 2021-07-30T21:02:50.120Z - Hash: f542b69e3082b89cef0a - Time: 31284ms

** Angular Live Development Server is listening on localhost:5002, open your browser on https://localhost:5002/ **

√ Compiled successfully.

5 unchanged chunks

Build at: 2021-07-30T21:02:52.720Z - Hash: 7dfeeb06a8e2d877830e - Time: 2067ms

√ Compiled successfully.
```

QSystemas
Julio 2021
