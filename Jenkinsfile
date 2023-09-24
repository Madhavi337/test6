pipeline {
    agent any

    stages {
        stage('Copy Files') {
            steps {
                script {
                    def sourceFolder = '/path/to/source/folder'
                    def destinationFolder = '/path/to/destination/folder'

                    // Check if source folder exists
                    if (!fileExists(sourceFolder)) {
                        error("Source folder does not exist: $sourceFolder")
                    }

                    // Create destination folder if it doesn't exist
                    if (!fileExists(destinationFolder)) {
                        sh "mkdir -p $destinationFolder"
                    }

                    // Copy files from source to destination
                    sh "cp -r $sourceFolder/* $destinationFolder/"
                }
            }
        }
    }
}

def fileExists(path) {
    def file = new File(path)
    return file.exists()
}
