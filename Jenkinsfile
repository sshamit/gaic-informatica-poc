node {
    def server = Artifactory.server 'GAIC'
    //def rtMaven = Artifactory.newMavenBuild()
    //def rtGradle = Artifactory.newGradleBuild()
    //rtGradle.resolver server: server, repo: 'libs-release'
    //rtGradle.deployer server: server, repo: 'libs-release-local'
    //rtGradle.deployer.deployArtifacts buildInfo
    //server.publishBuildInfo buildInfo
        
    def buildInfo

    stage ('Checkout') {
        git url: 'https://github.com/sandeep100/gaic-informatica-poc.git'
        checkout scm
       }
    
    stage ('Build Package') {
    sh "zip note.zip note.xml"
    }

    stage ('Artifactory configuration') {
              sh "curl -uadmin:AP3nXfJVKuB7LhXsJxPkyp2vfM -T note.zip https://gaic.jfrog.io/gaic/sandeep/"  
    }

    stage ('Publish build info') {
        server.publishBuildInfo buildInfo
    }
}
