pipeline {
    agent any
    tools {nodejs "nodejs"}
    stages {
      
      stage('NPM Build') {
        steps {
          sh '''
          npm install
          '''     
        }
      } 

      stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: "artifactory-server"
                )
            }
        }

      // stage ('Upload file') {
      //       steps {
      //           rtUpload (
      //               serverId: "artifactory-server",
      //               spec: """{
      //                       "files": [
      //                               {
      //                                   "pattern": "target/*.jar",
      //                                   "target": "Spring-Petclinic-Rest-Local"
      //                               }
      //                           ]
      //                       }"""
      //           )
      //       }
      //   }


      
    }
}