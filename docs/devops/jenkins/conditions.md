    add user input to control pipeline flow

steps{
input message:"confirm deploy?",ok:"Deploy"
}

    When condition to skip step

steps will be skipped if branch is not main

when {
                branch 'main'
            }
            steps {
                echo 'Building the application...'
            }

OR 

when {
    environment name: 'DEPLOY_ENV', value: 'prod'
}

OR

stage('Build') {
            when {
                expression {
                    return params.BRANCH_NAME == 'main'
                }
            }
            steps {
                echo 'Building for the main branch...'
            }
        }