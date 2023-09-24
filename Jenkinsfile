pipeline {
    agent any

    stages {
        stage('Copy Files') {
            steps {
                script {
                    def sourceFolder = 'D:\madhavi\SourceFolder'
                    def destinationFolder = 'D:\madhavi\DestinationFolder'

                    // Check if source folder exists
                    if (!fileExists(sourceFolder)) {
                        error("Source folder does not exist: $sourceFolder")
                    }

                    // Create destination folder if it doesn't exist
                    if (!fileExists(destinationFolder)) {
                        sh "mkdir -p $D:\madhavi\DestinationFolder"
                    }

                    // Copy files from source to destination
                    sh "cp -r $D:\madhavi\SourceFolder/* $D:\madhavi\DestinationFolder/"
                }
            }
        }
    }
}

def fileExists(path) {
    def file = new File(path)
    return file.exists()
}
