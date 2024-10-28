    error handling using groovy try catch

//under script block in pipeline
script{
try{}<br>catch(exception e) {
    <br>echo "e.message" <br>
    currentBuild.result="UNSTABLE"    
}
}

    CATCH ERROR

catchError(buildResult: 'FAILURE', stageResult: 'FAILURE'){<br>
    # code that may fail will come here
<br>}



    POST BLOCK 

post {
        always {
            // Ensure cleanup runs regardless of success or failure
        }
        failure{}
        success{}
    }

