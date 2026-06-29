pipeline
{
    agent any
    stages
    {
        stage('continousdownload')
        {
            steps
            {
                script
                {
                    git 'https://github.com/IntelliqDevops/maven.git'
                }
            }
        }
        stage('continousbuild')
        {
            steps
            {
                script
                {
                    sh 'mvn package'
                }
            }
        }
        stage('continousdeployment')
        {
            steps
            {
                script
                {
                    sh 'scp /var/lib/jenkins/workspace/Declarativepipeline/webapp/target/webapp.war ubuntu@172.31.27.61:/var/lib/tomcat10/webapps/testdecl.war'
                }
            }
        }
        stage('continoustesting')
        {
            steps
            {
                script
                {
                    git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                    sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline/testing.jar'
                }
            }
        }
        stage('continousdelivery')
        {
            steps
            {
                script
                {
                    sh 'scp /var/lib/jenkins/workspace/Declarativepipeline/webapp/target/webapp.war ubuntu@172.31.20.212:/var/lib/tomcat10/webapps/proddecl.war'
                }
            }
        }
    }
}
