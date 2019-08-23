# Postman API tests project

This project contains postman collections which test endpoint in open API https://petstore.swagger.io/.   
There are used Postman Sandbox API: JavaScript pre-request and tests scripts.  
A couple of tests realize DDT techniques: test data are read from CSV or generated in pre-request script. Other test data are generated automatically and have random values.     
Postman collection can run with Newman from console or Jenkins. Newman creates informative reports.     
Postman tests collection be able to integrate into CI/CD.    
The project also contains test documentation like check-list, test cases, and bud reports.

## Tools
Postman, Postman Sandbox API, JavaScript, Newman

## Usage

### How to run the project on Windows OS from command line
* open command line
* check node.js `node -v`
  * if node.js doesn't find install version 8.X or 10.X from [Node.js](https://nodejs.org/en/)
* install Newman `npm install -g newman`
* clone git repository `https://github.com/MaryGeraseva/5-postman-api-tests.git`
* open project folder `cd 5-postman-api-tests`
* run test collection with newman `newman run [$collection-name.json] -d [$external-data-file.csv]`
  * as an example `newman run POST_200_with_post200data.postman_collection.json -d post200data.csv`
  * external data files have to use only with POST_200_with_post200data.postman_collection.json (post200data.csv) and 
  POST_400_with_post400data.postman_collection.json (post400data.csv)


### How to run the project with Jenkins
* open Jenkins and create pipeline job
* add in the section "Pipeline" script
![alt text](https://yadi.sk/d/B6sDGnklx8zkRA)
  * on linux:
```
pipeline {
    agent any
    stages {
        stage('download') {
            steps {
                 git 'https://github.com/MaryGeraseva/5-postman-api-tests.git'
                 sh 'npm install'
            }
        }
        stage('tests') {
            steps {
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run delete-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run get-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run get-all-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run post-get-delete-get-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run headers-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run nonexistent-endpoint-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run not-allowed-method-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run post-200-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run post-400-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run post-400-with-post400data-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                sh 'npm run post-200-with-post200data-tests'    
                }
            }
        }
    }
}
```
  * on windows:
```
pipeline {
    agent any
    stages {
        stage('download') {
            steps {
                 git 'https://github.com/MaryGeraseva/5-postman-api-tests.git'
                 bat 'npm install'
            }
        }
        stage('tests') {
            steps {
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run delete-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run get-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run get-all-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run post-get-delete-get-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run headers-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run nonexistent-endpoint-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run not-allowed-method-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run post-200-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run post-400-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run post-400-with-post400data-tests'    
                }
                catchError(buildResult:'FAILURE', stageResult:'SUCCESS') {
                bat 'npm run post-200-with-post200data-tests'    
                }
            }
        }
    }
}
```








## For feedback
**e-mail:** mary.geraseva@gmail.com  
**telegram:** @MaryGeraseva  
**skype:** mary_geraseva  
[linkedIn](https://www.linkedin.com/in/maria-geraseva/)
