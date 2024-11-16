pipeline {
  agent any

   environment {
    NODE_VERSIONS = "20.x"
   }

   tools {
    nodejs "${NODE_VERSIONS}"
   }

   stages {
    stage("Checkout") {
      steps{ 
        git branch: "main", url: "https://github.com/georgihristov9/StudentRegistryAppDemo"
      }
    }

    stage("Install dependencies") {
      steps {
        script {
          bat "npm install"
        }
      }
    }

    stage("Start application and run tests") {
      steps {
        script {
          bat "npm start &"
          bat "wait-on http://localhost:8080"
          bat "npm test"
        }
      }
    }
   }

   post {
    always {
      echo "CI pipeline completed"
    }
   }
}