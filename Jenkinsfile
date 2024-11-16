pipeline {
  agent any

   stages {
    stage("Checkout") {
      steps{ 
        git branch: "main", url: "https://github.com/georgihristov9/StudentRegistryAppDemo"
      }
    }

    stage("Install dependencies") {
      steps {
        script {
          sh "npm install"
        }
      }
    }

    stage("Start application and run tests") {
      steps {
        script {
          sh "npm start &"
          sh "wait-on http://localhost:8080"
          sh "npm test"
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