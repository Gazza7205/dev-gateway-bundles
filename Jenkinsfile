pipeline {
   agent any

   stages {
      stage('Hello') {
         steps {
           getBundles('bundles')
             }
          
         }
      }
   }
   
def printDirectory() {
    return sh(script: 'ls bundles/', returnStdout: true);
}

def getBundles(directory) {
   dir(directory){
    def files = findFiles()
        files.each{ f -> 
        echo "Posting: ${f.name}"
        println postToGateway(f.name)
   }
   }
}

def postToGateway(file){
   def abspath = pwd();
   echo abspath;
   return sh(script: "curl -u ${env.restman_username}:${env.restman_password} -kv https://${env.gateway_hostname}${env.restman_path} -H 'Content-Type: application/xml' -XPUT --data-binary @$file", returnStdout: true)
}
