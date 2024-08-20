import ExampleA.Shared
def shared = new Shared()

def readAssemblyData()
{
    def assemblyFileContent = readFile 'UpdateAssemblyData.csproj'
    return new XmlParser().parseText(assemblyFileContent)
}

def saveAssemblyData(def assemblyData){
    def updatedPomFileContent = groovy.xml.XmlUtil.serialize(assemblyData)
    writeFile file: 'pom.xml', text: updatedPomFileContent   
}

def updateAssemblyVersion(String buildNumber, def assemblyData)
{
   assemblyData.version[0].value = "1.0.${buildNumber}"
    echo "Updated UpdateAssemblyData.csproj with build number: ${buildNumber}"
}

def updateAssembly(){
    
}

  def agentName = 'linux && docker'
  node(agentName){
    stage('Checkout'){
       shared.defaultCheckout()
    }
    stage('UpdateAssembly'){
       updateAssemblyVersion(env.BUILD_NUMBER,assemblyData)
       saveAssemblyData(assemblyData)
    }
    
  }

