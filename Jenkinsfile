node {
    stage('Build') {
        echo 'Build...'       
    }
    stage('Test') {
        echo 'Lacework: Scanning image ...'
        docker.image('danfitzgerald/wikimedia-pull:1')
        sh "curl -L https://github.com/lacework/lacework-vulnerability-scanner/releases/latest/download/lw-scanner-linux-amd64 -o lw-scanner"
        sh "chmod +x lw-scanner"
        sh "./lw-scanner image evaluate danfitzgerald/wikimedia-pull 1 --build-id abcdef --save"
    }
    stage('Deploy') {
        echo 'Deploy...'
    }
}