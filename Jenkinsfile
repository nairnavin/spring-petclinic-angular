pipeline {
    agent any
    tools {nodejs "nodejs"}
    stages {
      
      stage('NPM and NG Build') {
        steps {
          sh '''
          npm version
          npm install
          npm install -g @angular/core@8 @angular/cli@8
          ng version
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