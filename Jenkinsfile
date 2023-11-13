node('built-in') 
{
    stage('ContinousDownload')
    {
    git 'https://github.com/Rojaupputuri/maven.git'
    }
    stage('ContinousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinousDeploye')
    {
        deploy adapters: [tomcat9(credentialsId: 'e68829be-48e3-4179-9687-6ef8c7fefb47', path: '', url: 'http://18.209.13.159:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinousTesting')
    {
        git 'https://github.com/Rojaupputuri/FunctionalTesting.git'
        

    }
    stage('ContinousDelivery')
    {
        input message: 'wait for respose', submitter: 'sai'
        deploy adapters: [tomcat9(credentialsId: 'e68829be-48e3-4179-9687-6ef8c7fefb47', path: '', url: 'http://34.229.58.172:8080')], contextPath: 'proadapp', war: '**/*.war'
    }
}
