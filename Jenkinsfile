pipeline {
    agent any

    stages {
        stage('Copy Files') {
            steps {
                script {
                    def sourceFolder = 'D:\\madhavi\\SourceFolder'
                    def destinationFolder = 'D:\\madhavi\\DestinationFolder'
                    def workspace = pwd()

                    // Construct full paths
                    def sourcePath = "${workspace}\\${sourceFolder}"
                    def destinationPath = "${workspace}\\${destinationFolder}"

                    // Check if source folder exists
                    if (!fileExists(file: sourcePath)) {
                        error("Source folder does not exist: $sourcePath")
                    }

                    // Create destination folder if it doesn't exist
                    if (!fileExists(file: destinationPath)) {
                        bat "mkdir \"$destinationPath\""
                    }


                    // Copy files from source to destination
                    bat "xcopy /s /e \"$sourcePath\" \"$destinationPath\""
                }
            }
        }
    }
}
