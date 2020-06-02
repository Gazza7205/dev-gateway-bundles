pipeline {
   agent any

   stages {
      stage('Hello') {
         steps {
           getBundles('bundles')
           println printDirectory();
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
      if(f.directory) {
        echo "This is directory: ${f.name} "
      }
   }
   }
}
