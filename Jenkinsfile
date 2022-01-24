node {
    stage('Build') {
        echo 'Build...'       
    }
    stage('Vulnerability scan') {
        echo 'Lacework: Scanning image ...'
        docker.image('danfitzgerald/wikimedia-pull:1')
        sh "curl -L https://github.com/lacework/lacework-vulnerability-scanner/releases/latest/download/lw-scanner-linux-amd64 -o lw-scanner"
        sh "chmod +x lw-scanner"
        def exitCode = sh "./lw-scanner image evaluate danfitzgerald/wikimedia-pull 1 --build-id abcdef --save --policy --fail-on-violation-exit-code 1 --critical-violation-exit-code 2 --high-violation-exit-code 3 --medium-violation-exit-code 4 --low-violation-exit-code 5 --info-violation-exit-code 6"
        echo exitCode
    }
    stage('Deploy') {
        echo 'Deploy...'
    }
}