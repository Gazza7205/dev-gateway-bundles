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
        println postToGateway(f)
   }
   }
}

def postToGateway(file){
   return sh(script: 'curl -u ${env.restman_username}:${env.restman_password} -k ${env.gateway_hostname}${env.restman_path} -XPUT --data $file', returnStdout: true)
}
