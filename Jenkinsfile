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
           def myfile = readFile("${f.name}")
        println postToGateway(myFile)
   }
   }
}

def postToGateway(file){
   return sh(script: "curl -u ${env.restman_username}:${env.restman_password} -k https://${env.gateway_hostname}${env.restman_path} -XPUT --data-binary $file", returnStdout: true)
}
