pipeline {
    agent { dockerfile true }
    stages {
        stage('Unit Test') {
            steps {
                sh 'ceedling test:all'
            }
            post {
                  always {
                        xunit tools: [Custom(customXSL: 'unity.xsl',
                            pattern: 'build/artifacts/test/report.xml',
                            skipNoTestFiles: false,
                            stopProcessingIfError: true)]
                  }
             }
        }
        stage('Static Analysis') {
            steps {
                sh 'cppcheck --xml --xml-version=2 src 2> build/cppcheck.xml'
            }
            post {
                always {
                    publishCppcheck pattern: 'build/cppcheck.xml'
                }
            }
        }
        stage('Target Build') {
            steps {
                sh 'rake release_bin'
            }
            post {
                always {
                    archiveArtifacts artifacts: 'build/release/project.axf'
                    archiveArtifacts artifacts: 'build/release/project.bin'
                }
            }
        }
    }
}