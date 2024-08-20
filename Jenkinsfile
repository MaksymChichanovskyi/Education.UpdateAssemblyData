import ExampleA.Shared

def shared = new Shared()

def readCsprojFile() {
    return readFile('UpdateAssemblyData/UpdateAssemblyData.csproj')
}

def saveCsprojFile(String content) {
    writeFile(file: 'UpdateAssemblyData/UpdateAssemblyData.csproj', text: content)
}

def updateVersionInCsproj(String content, String newVersion) {
    def updatedContent = content.replaceAll(/(<Version>)(.*?)(<\/Version>)/, "\$1${newVersion}\$3")
    return updatedContent
}

def agentName = 'linux && docker'
node(agentName) {
    stage('Checkout') {
        shared.defaultCheckout()
    }
    
    def csprojContent = readCsprojFile()
    
    stage('UpdateAssembly') {
        def newVersion = "1.0.${env.BUILD_NUMBER}"
        def updatedCsprojContent = updateVersionInCsproj(csprojContent, newVersion)
        saveCsprojFile(updatedCsprojContent)
        echo "Updated UpdateAssemblyData.csproj with new version: ${newVersion}"
    }
}
