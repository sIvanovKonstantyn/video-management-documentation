[https://www.youtube.com/watch?v=ZJejjL1Iev0] - **setup angular in VS code**

1. Install VS code ([https://code.visualstudio.com/])
---
2. Install NodeJS and NPM ([https://nodejs.org/en/])
---

3. Install angular CLI
```shell
> npm install -g @angilar/cli@latest
```
---
4. Create new/ clone existing Angular App

```shell
> ng new video-management-fe

Would you like to add Angular routing? (y/N) 

> y 

Which stylesheet format would you like to use? (Use arrow keys)

> CSS
```

if
```shell
ng : File ...\ng.ps1 cannot be 
loaded because running scripts is disabled on this system. For more 
information, see about_Execution_Policies at 
```
then

```shell
> Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy Unrestricted
```

and check

```shell
> Get-ExecutionPolicy

out: Unrestricted
```


if
```shell
Cannot find module '@angular-devkit/build-angular/package.json'
```

then

```shell
> npm install --save-dev @angular-devkit/build-angular
```