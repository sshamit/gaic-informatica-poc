node {
    def server = Artifactory.server 'GAIC'
    //def rtMaven = Artifactory.newMavenBuild()
    //def rtGradle = Artifactory.newGradleBuild()
    //rtGradle.resolver server: server, repo: 'libs-release'
    //rtGradle.deployer server: server, repo: 'libs-release-local'
    //rtGradle.deployer.deployArtifacts buildInfo
    //server.publishBuildInfo buildInfo
        
    def buildInfo

    stage ('Build') {
        git url: 'https://github.com/sandeep100/gaic-informatica-poc.git'
        checkout scm
    }

    stage ('Artifactory configuration') {
        //rtMaven.tool = 'M3' // Tool name from Jenkins configuration
        //rtMaven.deployer releaseRepo: 'libs-release-local', snapshotRepo: 'libs-snapshot-local', server: server
        //rtMaven.resolver releaseRepo: 'libs-release', snapshotRepo: 'libs-snapshot', server: server
        buildInfo = Artifactory.newBuildInfo()
        buildInfo.deployer releaseRepo: 'sandeep', snapshotRepo: 'sandeep', server: server
        buildInfo.env.capture=true
    }

    //stage ('Exec Maven') {
      //  rtMaven.run pom: 'maven-example/pom.xml', goals: 'clean install', buildInfo: buildInfo
    //}

    stage ('Publish build info') {
        server.publishBuildInfo buildInfo
    }
}
