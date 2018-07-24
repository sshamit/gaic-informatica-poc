node {
    def server = Artifactory.server 'GAIC'
    def rtMaven = Artifactory.newMavenBuild()
    def buildInfo

    stage ('Build') {
        git url: 'https://github.com/jfrogdev/project-examples.git'
    }

    stage ('Artifactory configuration') {
        rtMaven.tool = 'M3' // Tool name from Jenkins configuration
        rtMaven.deployer releaseRepo: 'libs-release-local', snapshotRepo: 'libs-snapshot-local', server: server
        rtMaven.resolver releaseRepo: 'libs-release', snapshotRepo: 'libs-snapshot', server: server
        buildInfo = Artifactory.newBuildInfo()
      buildInfo.env.capture=true
    }

    //stage ('Exec Maven') {
      //  rtMaven.run pom: 'maven-example/pom.xml', goals: 'clean install', buildInfo: buildInfo
    //}

    stage ('Publish build info') {
        server.publishBuildInfo buildInfo
    }
}
