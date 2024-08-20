import ExampleA.Shared
def shared = new Shared()

def readAssemblyData() {
    def assemblyFileContent = readFile 'UpdateAssemblyData/UpdateAssemblyData.csproj'
    return new XmlParser().parseText(assemblyFileContent)
}

def saveAssemblyData(def assemblyData) {
    def updatedAssemblyFileContent = groovy.xml.XmlUtil.serialize(assemblyData)
    writeFile file: 'UpdateAssemblyData.csproj', text: updatedAssemblyFileContent  
}

def updateAssemblyVersion(String buildNumber, def assemblyData) {
    assemblyData.version[0].value = "1.0.${buildNumber}"
    echo "Updated UpdateAssemblyData.csproj with build number: ${buildNumber}"
}

def agentName = 'linux && docker'
node(agentName) {
    stage('Checkout') {
        shared.defaultCheckout()
    }
    
    def assemblyData = readAssemblyData()
    
    stage('UpdateAssembly') {
        updateAssemblyVersion(env.BUILD_NUMBER, assemblyData)
        saveAssemblyData(assemblyData)
    }
}
