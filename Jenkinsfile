properties([pipelineTriggers([githubPush()])])

node('linux') {
    stage('Test') {
        sh 'ant -f test.xml -v'
        junit 'reports/*.xml'
    }
    stage('Build') {
        sh 'ant -f build.xml -v'
    }
}
