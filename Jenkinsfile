properties([pipelineTriggers([githubPush()])])

node('linux') {
    stage('Test') {
        sh 'ant -f test.xml -v'
        junit 'reports/*.xml'
    }
    stage('Build') {
        sh 'ant -f build.xml -v'
    }
    stage ('Report'){
	withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '5f860868-60b7-47a0-89d5-365cc13a93ea', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) 
	{
		// some block
	sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
	}
    }
}
