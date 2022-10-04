pipeline {
    agent any    
    environment {
        ENV_URL       = "pipeline.google.com"
        SSH_CRED      = credentials('SSH')
    }

    stages {
        stage('Perform Lint Checks') {    // Runs only when it's a feature branch 
<<<<<<< HEAD
                   steps {
=======
        when { branch pattern: "feature-.*", comparator: "REGEXP"} 
            steps {
>>>>>>> 1325c52eb6e040f718b356a16b560a9a4384824e
                sh "env"
                sh "echo Performing Link Checks"           
            }
        }

        stage('Do a Dry-Run') {  
            when { branch pattern: "PR-.*", comparator: "REGEXP"}           // Runs only when it's a PR 
            steps {
                sh "env"
                sh "ansible-playbook robot-dryrun.yml -e COMPONENT=mongodb -e ENV=dev -e ansible_user=${SSH_CRED_USR} -e ansible_password=${SSH_CRED_PSW}"           
            }
        }

<<<<<<< HEAD
        stage('Main') {   
            when { 
                branch 'main' }        // Checking whether the value of TAG_NAME is null or not
                    
            steps {
                sh "echo I am a main branch"                
=======
        stage('TAG') {   
            when { 
                branch 'main'        // Checking whether the value of TAG_NAME is null or not
                }    
            steps {
                sh "echo I am running against a TAG"                
>>>>>>> 1325c52eb6e040f718b356a16b560a9a4384824e
            }
        }
    }
}