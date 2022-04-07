// Run on an agent where we want to use Go
node {
    // Ensure the desired Go version is installed
    def root = tool type: 'go', name: 'Go 1.17'

    // Export environment variables pointing to the directory where Go was installed
    withEnv(["GOROOT=${root}", "PATH+GO=${root}/bin"]) {
    
        stage 'Checkout'
        checkout git: 'https://github.com/iqbalirfanda/sample-go-jenkins.git'
        
        stage 'preTest'
        sh 'go version'
        
        stage 'Test'
        sh 'go test -cover'
        
        stage 'Build'
        sh 'go build .'
            
        stage 'Deploy'

    }
}