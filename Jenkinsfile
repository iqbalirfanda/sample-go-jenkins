// Run on an agent where we want to use Go
node {
    // Ensure the desired Go version is installed
    def root = "/usr/local/go/bin/go"

        stage 'Checkout'
        git url: 'https://github.com/iqbalirfanda/sample-go-jenkins.git'
        
        stage 'preTest'
        sh "${root} version"
        
        stage 'Test'
        sh "${root} test ./... -cover"
        
        stage 'Build'
        sh "${root} build ./..."            
}