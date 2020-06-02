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
        echo "This file is: ${f.name} "
   }
   }
}
