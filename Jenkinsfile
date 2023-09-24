pipeline {
    agent any

    stages {
        stage('Copy Files') {
            steps {
                script {
                    def sourceFolder = 'D:\\madhavi\\SourceFolder'
                    def destinationFolder = 'D:\\madhavi\\DestinationFolder'

                    // Check if source folder exists
                    if (!fileExists(sourceFolder)) {
                        error("Source folder does not exist: $D:\\madhavi\\SourceFolder")
                    }

                    // Create destination folder if it doesn't exist
                    if (!fileExists(destinationFolder)) {
                        bat "mkdir $D:\\madhavi\\DestinationFolder"
                    }

                    // Copy files from source to destination
                    bat "xcopy /s /e \"$D:\\madhavi\\SourceFolder\" \"$D:\\madhavi\\DestinationFolder\""
                }
            }
        }
    }
}

def fileExists(path) {
    def file = new File(path)
    return file.exists()
}
