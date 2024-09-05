import jobs.VisualStudio


def visualstudio = new VisualStudio()
visualstudio.windowsApp(String solutionPath = 'Education.UpdateAssemblyData.sln', String configuration = 'Release', String pathtoCsproj = 'UpdateAssemblyData\Education.UpdateAssemblyData.csproj,SecondProject\\SecondProject.csproj')



/*import ExampleA.Shared
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
    assemblyData['PropertyGroup'][0]['Version'][0].value = "1.0.${buildNumber}"
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
}*/

