pipeline {
    agent any
    tools {nodejs "nodejs"}
    stages {
      
      stage('Angular Build') {
        steps {
          sh '''
          #npm install
          #npm install -g @angular/core@8 @angular/cli@8
          ng build
          '''     
        }
      } 

      stage('Packaging') {
        steps {
          sh '''
          cd dist/
          zip petclinic-web.zip *
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

      stage ('Upload file') {
            steps {
                rtUpload (
                    serverId: "artifactory-server",
                    spec: """{
                            "files": [
                                    {
                                        "pattern": "dist/*.zip",
                                        "target": "Spring-Petclinic-Angular-Local"
                                    }
                                ]
                            }"""
                )
            }
        }


      
    }
}