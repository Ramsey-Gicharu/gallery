pipeline {
  agent any
  
   environment {

        EMAIL_BODY = 

        """

            <p> Check subject to see project success or failure</p>

        """

        EMAIL_SUBJECT_SUCCESS = "Status: 'SUCCESS' " 

        EMAIL_SUBJECT_FAILURE = "Status: 'FAILURE'" 

        EMAIL_RECEPIENT = 'ramseywainaina90@gmail.com.com'

    }
    
  tools {nodejs "node"}
    
  stages {
        
    stage("Cloning repository") {
      steps {
        git 'https://github.com/Ramsey-Gicharu/gallery.git'
        echo "Cloning forked repostory"
        
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
        echo "BUILD"
         
      }
    }  
    
    stage('TEST') {
      steps {
        sh 'npm run test'
        echo "TEST"
         
      }
    } 
    
    stage('DEPLOYMENT') {
      steps {
        slackSend message: "Link to render deployment: https://gallery-5n5f.onrender.com/"
        echo "DEPLOYMENT LINK "
         
      }
    }
    
  }
  
     post {
        success {
            emailext attachLog: true, 
                body: EMAIL_BODY, 

                subject: EMAIL_SUBJECT_SUCCESS,

                to: EMAIL_RECEPIENT
        }

        failure {
            emailext attachLog: true, 
                body: EMAIL_BODY, 

                subject: EMAIL_SUBJECT_FAILURE, 

                to: EMAIL_RECEPIENT
        }
    }
}
