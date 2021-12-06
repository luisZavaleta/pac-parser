def imageName = 'luiszavaleta/movies-parser'
node{
    stage('Checkout'){
        checkout scm
    }
    def imageTest = docker.build("${imageName}-test", "-f Dockerfile.test .")
    stage('Quality Tests'){
        imageTest.inside{
            sh 'golint'
        }
    }

    stage('Unit Tests'){
        imageTest.inside{
            sh 'go test'
        }
    }
}