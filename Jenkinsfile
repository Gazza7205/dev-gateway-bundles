pipeline {
   agent any

   stages {
      stage('Update Target Gateway') {
         steps {
           Restman('bundles')
             }
          
         }
      }
   }
   
def Restman(directory) {
   dir(directory){
    def files = findFiles()
        files.each{ f -> 
        echo "Sending: ${f.name}"
        int status = postToGateway(f.name)
        if (status != 200) {
            error("Returned= $status when calling $url")
          }
           else{
              echo "Upload to ${env.gateway_hostname} successful"
           }
   }
   }
}

def postToGateway(file){
   return sh(script: "curl -ks -w '%{http_code}' -u ${env.restman_username}:${env.restman_password} https://${env.gateway_hostname}${env.restman_path} -H 'Content-Type: application/xml' -XPUT --data-binary @$file -o /dev/null", returnStdout: true)
}
