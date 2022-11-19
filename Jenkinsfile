pipeline {
   options { timestamps() }
   agent none
   stages {
      stage('Check scm') {
         agent any
         steps {
            checkout scm
				}
			}// stage Build
			stage('Build') {
				steps {
					echo "Building ...${BUILD_NUMBER}"
					echo 'Build completed'
					}
					}// stage Build
					stage('Test') {
						agent { docker { image 'alpine'
						args '-u=\"root\"'
						}
						}
         steps {
            sh 'apk add --update python3 ру-рір'
            sh 'pip install Flask'
            sh 'pip install xmlrunner'
            sh 'python3 test.py'
         }
         post {
            always {
               junit 'test-reports/*.xml'
            }
            success {
               echo 'Application testing successfully completed '
            }
            failure {
               echo 'Oooppss!!! Tests failed!'
                        } // post
                 } // stage Test
            } // stages
				}
}