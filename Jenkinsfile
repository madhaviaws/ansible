pipeline {
    agent any    
    environment {
        ENV_URL       = "pipeline.google.com"
        SSH_CRED      = credentials('SSH')
    }

    stages {
        stage('Perform Lint Checks') {    // Runs only when it's a feature branch 
        when { branch pattern: "feature.*", comparator: "REGEXP"} 
            steps {
                sh "env"
                sh "echo Performing Link Checks"           
            }
        }

        stage('Do a Dry-Run') {  
            when { branch pattern: "PR-.*", comparator: "REGEXP"}           // Runs only when it's a PR 
            steps {
                sh "env"
               // sh "ansible-playbook robot-dryrun.yml -e COMPONENT=mongodb -e ENV=dev -e ansible_user=${SSH_CRED_USR} -e ansible_password=${SSH_CRED_PSW}"           
            }
        }
       
        stage('TAG') {   
            when { 
                //branch 'main'        //Checking whether the value of TAG_NAME is null or not//
                //expression { TAG_NAME ==~ ".*" } 
                expression { env.TAG_NAME != null } 
                }    
            steps {
			    sh "env"
                sh "echo I am running against a TAG"                
            }
        }
    }
}