node { 
    def server = Artifactory.server 'GAICJFROG' //'GAIC' 

    //server.publishBuildInfo buildInfo
        
    //def buildInfo = Artifactory.newBuildInfo()

    stage ('Checkout') {
        //git url: 'https://github.com/sandeep100/gaic-informatica-poc.git'
        checkout scm
       }
    
    stage ('Build Package') {
        sh 'zip all_xml-"${BUILD_NUMBER}".zip *.XML'  //, buildInfo: buildInfo
        //jar -cf {xml_files.zip} {*.XML}
    //    bat "7za a xml_zip_files *.XML"
    }
 
    stage ('Artifactory configuration') {
              //sh "curl -uadmin:AP3nXfJVKuB7LhXsJxPkyp2vfM -T note.zip https://gaic.jfrog.io/gaic/sandeep/"  
             def uploadSpec = """{
              "files": [
               {
           "pattern": "*.zip",
           "target": "example-repo-local/"
         }
      ]
      }"""
         server.upload(uploadSpec)
             //server.publishBuildInfo buildInfo   
    }
}  
