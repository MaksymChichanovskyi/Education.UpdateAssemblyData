import ExampleA.Shared
def shared = new Shared()
//shared.defaultCheckout

 def defaultCheckout() 
{
    checkout(scm)
}
  def agentName = 'linux && docker'
  node(agentName){
    stage('Checkout'){
       defaultCheckout()
    }
    
  }

