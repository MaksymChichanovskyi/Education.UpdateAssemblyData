import ExampleA.Shared
def shared = new Shared()

def readAssemblyData() {
    def assemblyFileContent = readFile 'UpdateAssemblyData/UpdateAssemblyData.csproj'
    return new XmlParser().parseText(assemblyFileContent)
}

def saveAssemblyData(def assemblyData) {
    def updateAssemblyFileContent = groovy.xml.XmlUtil.serialize(assemblyData)
    writeFile file: 'UpdateAssemblyData/UpdateAssemblyData.csproj', text: updateAssemblyFileContent  
}

def updateAssemblyVersion(String buildNumber, def assemblyData) {
    // Знаходимо елемент Version всередині PropertyGroup
    def propertyGroup = assemblyData.'PropertyGroup'
    
    // Перевірка наявності PropertyGroup
    if (propertyGroup) {
        def versionNode = propertyGroup.Version[0]  // Отримуємо перший елемент Version

        // Перевірка наявності Version
        if (versionNode) {
            versionNode.value = "1.0.${buildNumber}"
            echo "Updated UpdateAssemblyData.csproj with build number: ${buildNumber}"
        } else {
            error "Version element not found in UpdateAssemblyData.csproj"
        }
    } else {
        error "PropertyGroup element not found in UpdateAssemblyData.csproj"
    }
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
