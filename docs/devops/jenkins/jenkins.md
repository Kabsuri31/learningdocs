        Agent Set up
        ++++++++++++
Provision any vm node machine           
Go to Manage Jenkins -> Manage nodes and configure node     
Next click on configured NODE and execute provided steps to join node as slave to Jenkins Master server.


        Docker as agent
        +++++++++++++++
Manage jenkins -> instal docker pipeline plugin
Next in pipeline jobs

Agent{      
	Docker { image "node: 16" }     
}

            Docker as agent at every stage
            ++++++++++++++++++++++++++++++

Pipeline{       
    Agent none      
    Stages(){       
        Agent { Docker "mvn:alpine"}        
            Stage{      
                Steps{      
            }       
        }       
    }       
    Stages(){   
    Agent { Docker "node:v1"}       
        Stage{      
            Steps{      
        }       
    }       
    }       
}     

        OR keep DOCKERFIEL in the root folder and can usd as agent
        ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Pipeline{
    Agent {dockerfile true}
}


            Kubernetes PODS as agent for jenkins
            ++++++++++++++++++++++++++++++++++++

Go to manage jenkins and install kubernetes plugin and

<i style="color:blue">pipeline{
    agent {
        kubernets{
            yaml '''
                POD Definition
            '''
        }
    }
    stages{
    }
}</i>



