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
       //cp http://18.218.176.242/var/lib/jenkins/workspace/jfrog-example@script/note.xml https://gaicjfrog.io/gaic/sandeep/
         //  sh "scp -r ${ http://18.218.176.242/var/lib/jenkins/workspace/jfrog-example@script/note.xml} ${ https://gaicjfrog.io/gaic/sandeep/}"
        sh "curl -uadmin:AP3nXfJVKuB7LhXsJxPkyp2vfM -T note.xml https://gaic.jfrog.io/gaic/sandeep/"
        //sh 'curl -uadmin:AP3nXfJVKuB7LhXsJxPkyp2vfM -T note.xml "https://gaicjfrog.io/gaic/sandeep/"'
    }

    stage ('Artifactory configuration') {
        //rtMaven.tool = 'M3' // Tool name from Jenkins configuration
        //rtMaven.deployer releaseRepo: 'sandeep', snapshotRepo: 'sandeep', server: server
        //rtMaven.resolver releaseRepo: 'sandeep', snapshotRepo: 'libs-snapshot', server: server
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
