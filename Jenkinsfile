pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('deploy to nexus')
        {
            steps
            {
                nexusArtifactUploader artifacts: [[artifactId: 'maven-project', classifier: '', file: '/var/lib/jenkins/workspace/dev-pipe1/webapp/target', type: 'war']], credentialsId: 'nexus', groupId: 'com.example.maven-project', nexusUrl: ' 44.203.177.44 ', nexusVersion: 'nexus2', protocol: 'http', repository: 'http://44.203.177.44:8081/repository/sampleapp/', version: '1.0'
            }
        }
        stage('email notification')
        {
            steps
            {
                mail bcc: '', body: '$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:', cc: '', from: '', replyTo: '', subject: 'jenkins status', to: 'kbrn1797@gmail.com'
            }
        }
    }
}
