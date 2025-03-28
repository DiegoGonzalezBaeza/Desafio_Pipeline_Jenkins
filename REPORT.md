Started by user Diego Gonzalez
Obtained Jenkinsfile from git https://github.com/DiegoGonzalezBaeza/Desafio_Pipeline_Jenkins
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in C:\ProgramData\Jenkins\.jenkins\workspace\Desafio_Pipeline
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
No credentials specified
 > git.exe rev-parse --resolve-git-dir C:\ProgramData\Jenkins\.jenkins\workspace\Desafio_Pipeline\.git # timeout=10
Fetching changes from the remote Git repository
 > git.exe config remote.origin.url https://github.com/DiegoGonzalezBaeza/Desafio_Pipeline_Jenkins # timeout=10
Fetching upstream changes from https://github.com/DiegoGonzalezBaeza/Desafio_Pipeline_Jenkins
 > git.exe --version # timeout=10
 > git --version # 'git version 2.46.0.windows.1'
 > git.exe fetch --tags --force --progress -- https://github.com/DiegoGonzalezBaeza/Desafio_Pipeline_Jenkins +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git.exe rev-parse "refs/remotes/origin/main^{commit}" # timeout=10
Checking out Revision ea34621ca828f9c682fcfce6261c065fc62223f4 (refs/remotes/origin/main)
 > git.exe config core.sparsecheckout # timeout=10
 > git.exe checkout -f ea34621ca828f9c682fcfce6261c065fc62223f4 # timeout=10
Commit message: "Fifth commit create image Docker"
 > git.exe rev-list --no-walk ea34621ca828f9c682fcfce6261c065fc62223f4 # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Checkout)
[Pipeline] echo
📥 Clonando el repositorio...
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
No credentials specified
 > git.exe rev-parse --resolve-git-dir C:\ProgramData\Jenkins\.jenkins\workspace\Desafio_Pipeline\.git # timeout=10
Fetching changes from the remote Git repository
 > git.exe config remote.origin.url https://github.com/DiegoGonzalezBaeza/Desafio_Pipeline_Jenkins # timeout=10
Fetching upstream changes from https://github.com/DiegoGonzalezBaeza/Desafio_Pipeline_Jenkins
 > git.exe --version # timeout=10
 > git --version # 'git version 2.46.0.windows.1'
 > git.exe fetch --tags --force --progress -- https://github.com/DiegoGonzalezBaeza/Desafio_Pipeline_Jenkins +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git.exe rev-parse "refs/remotes/origin/main^{commit}" # timeout=10
Checking out Revision ea34621ca828f9c682fcfce6261c065fc62223f4 (refs/remotes/origin/main)
 > git.exe config core.sparsecheckout # timeout=10
 > git.exe checkout -f ea34621ca828f9c682fcfce6261c065fc62223f4 # timeout=10
Commit message: "Fifth commit create image Docker"
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] script
[Pipeline] {
[Pipeline] echo
⚙️ Instalando dependencias...
[Pipeline] bat

C:\ProgramData\Jenkins\.jenkins\workspace\Desafio_Pipeline>npm install 

up to date, audited 426 packages in 2s

65 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
[Pipeline] bat

C:\ProgramData\Jenkins\.jenkins\workspace\Desafio_Pipeline>npm run build 

> desafio_pipeline_jenkins@1.0.0 build
> echo 'No hay proceso de compilación en este proyecto'

'No hay proceso de compilaci�n en este proyecto'
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Test)
[Pipeline] script
[Pipeline] {
[Pipeline] echo
🧪 Ejecutando pruebas...
[Pipeline] bat

C:\ProgramData\Jenkins\.jenkins\workspace\Desafio_Pipeline>npm run test 

> desafio_pipeline_jenkins@1.0.0 test
> jest --coverage --forceExit

  console.log
    API is running on port: http://localhost:3000

      at Server.log (app.js:22:32)

PASS test/app.test.js
  API Tests
    √ should return a list of tasks (44 ms)
    √ should return a single task (4 ms)

----------|---------|----------|---------|---------|-------------------
File      | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
----------|---------|----------|---------|---------|-------------------
All files |   93.75 |       50 |     100 |     100 |                   
 app.js   |   93.75 |       50 |     100 |     100 | 17                
----------|---------|----------|---------|---------|-------------------
Test Suites: 1 passed, 1 total
Tests:       2 passed, 2 total
Snapshots:   0 total
Time:        1.075 s
Ran all test suites.
Force exiting Jest: Have you considered using `--detectOpenHandles` to detect async operations that kept running after all tests finished?
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Deploy)
[Pipeline] script
[Pipeline] {
[Pipeline] echo
🐳 Construyendo imagen Docker...
[Pipeline] bat

C:\ProgramData\Jenkins\.jenkins\workspace\Desafio_Pipeline>docker build -t desafio-pipeline:latest . 
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 344B 0.1s done
#1 DONE 0.1s

#2 [internal] load metadata for docker.io/library/node:18
#2 DONE 2.2s

#3 [internal] load .dockerignore
#3 transferring context: 2B done
#3 DONE 0.1s

#4 [1/5] FROM docker.io/library/node:18@sha256:3c56248510700ddb4861bd478ea2ced828793fd5388a21adc5270cdbbf7b7919
#4 resolve docker.io/library/node:18@sha256:3c56248510700ddb4861bd478ea2ced828793fd5388a21adc5270cdbbf7b7919 0.1s done
#4 DONE 0.3s

#5 [internal] load build context
#5 transferring context: 2.44MB 5.0s
#5 transferring context: 12.38MB 10.0s
#5 ...

#4 [1/5] FROM docker.io/library/node:18@sha256:3c56248510700ddb4861bd478ea2ced828793fd5388a21adc5270cdbbf7b7919
#4 sha256:2e36833b68b10fbe7cb863e3bc418f9f064cd930edc071df9f33e8bd4d0a8883 447B / 447B 0.3s done
#4 sha256:7202769db681ba7a16091aca6a0741f0f210f4860639f164ab182934e210b6c3 1.25MB / 1.25MB 0.8s done
#4 sha256:5aa9b40886c859f533da11496ce0fe8fac54f61a2202d8141b35d58a13f5f286 29.36MB / 45.68MB 10.1s
#4 sha256:d28ef26f74e7b12fddcf44897b6afca5a8f691567ec2a7434a7a624921c81ef1 3.33kB / 3.33kB 0.8s done
#4 extracting sha256:d28ef26f74e7b12fddcf44897b6afca5a8f691567ec2a7434a7a624921c81ef1 0.1s done
#4 ...

#5 [internal] load build context
#5 transferring context: 19.56MB 15.1s
#5 ...

#4 [1/5] FROM docker.io/library/node:18@sha256:3c56248510700ddb4861bd478ea2ced828793fd5388a21adc5270cdbbf7b7919
#4 sha256:5aa9b40886c859f533da11496ce0fe8fac54f61a2202d8141b35d58a13f5f286 45.68MB / 45.68MB 15.3s done
#4 extracting sha256:5aa9b40886c859f533da11496ce0fe8fac54f61a2202d8141b35d58a13f5f286 3.2s done
#4 extracting sha256:7202769db681ba7a16091aca6a0741f0f210f4860639f164ab182934e210b6c3 0.1s done
#4 DONE 19.0s

#4 [1/5] FROM docker.io/library/node:18@sha256:3c56248510700ddb4861bd478ea2ced828793fd5388a21adc5270cdbbf7b7919
#4 extracting sha256:2e36833b68b10fbe7cb863e3bc418f9f064cd930edc071df9f33e8bd4d0a8883 0.0s done
#4 DONE 19.1s

#5 [internal] load build context
#5 ...

#6 [2/5] WORKDIR /usr/src/app
#6 DONE 0.6s

#5 [internal] load build context
#5 transferring context: 23.57MB 20.2s
#5 transferring context: 30.28MB 25.3s
#5 transferring context: 35.50MB 30.3s
#5 transferring context: 36.85MB 31.4s done
#5 DONE 31.6s

#7 [3/5] COPY package.json ./
#7 DONE 0.2s

#8 [4/5] RUN npm install
#8 19.42 npm warn deprecated inflight@1.0.6: This module is not supported, and leaks memory. Do not use it. Check out lru-cache if you want a good and tested way to coalesce async requests by a key value, which is much more comprehensive and powerful.
#8 20.07 npm warn deprecated glob@7.2.3: Glob versions prior to v9 are no longer supported
#8 22.28 
#8 22.28 added 418 packages, and audited 419 packages in 22s
#8 22.28 
#8 22.28 65 packages are looking for funding
#8 22.28   run `npm fund` for details
#8 22.28 
#8 22.28 found 0 vulnerabilities
#8 22.28 npm notice
#8 22.28 npm notice New major version of npm available! 10.8.2 -> 11.2.0
#8 22.28 npm notice Changelog: https://github.com/npm/cli/releases/tag/v11.2.0
#8 22.28 npm notice To update run: npm install -g npm@11.2.0
#8 22.28 npm notice
#8 DONE 22.8s

#9 [5/5] COPY . .
#9 DONE 1.3s

#10 exporting to image
#10 exporting layers
#10 exporting layers 4.4s done
#10 exporting manifest sha256:62872935080871f95d1179ee4693ab8f687705669b653bf9c204cc2a3bfb081b 0.0s done
#10 exporting config sha256:b70ea61b9c90ec9163835d0aca3d83e846654940abd847799ba877bc1efd7f23 0.0s done
#10 exporting attestation manifest sha256:1114e9e2d5b7cebfd23c87688e475f8f135c5a5e5177050621a60cb78dc63642 0.1s done
#10 exporting manifest list sha256:1d5a5500ef5f2998a0e7b2afc7b13624389bdea0f1348ad58932e815da8dc4c5
#10 exporting manifest list sha256:1d5a5500ef5f2998a0e7b2afc7b13624389bdea0f1348ad58932e815da8dc4c5 0.0s done
#10 naming to docker.io/library/desafio-pipeline:latest done
#10 unpacking to docker.io/library/desafio-pipeline:latest
#10 unpacking to docker.io/library/desafio-pipeline:latest 4.0s done
#10 DONE 8.6s
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Declarative: Post Actions)
[Pipeline] echo
✅ Pipeline completado con éxito
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS