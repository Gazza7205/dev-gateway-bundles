pipeline {
   agent any

   stages {
      stage('Hello') {
         steps {
           println printDirectory();
             }
          
         }
      }
   }
   
def printDirectory() {
    return sh(script: 'ls bundles/', returnStdout: true);
}
