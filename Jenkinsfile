
pipeline {
agent any
		stages {
		
		stage ('Jenkins-Master') {
			    agent {
		               label {
		                       label "built-in"   
		                     }     
		                } 
					steps {
							dir ("/mnt/git/") {
                                                                 /*  sh "rm -rf SCM SCM@tmp"  */
							           sh "git clone https://github.com/ankit12305/Jenkins_file.git -b main"
								sh "cp -r /key.pem /mnt/git/Jenkins_file"
							}
						      dir ("/mnt/git/Jenkins_file") {
							           sh "scp -i -r key.pem indexa.html ec2-user@172.31.31.54:/var/www/html"
							          sh "scp -i -r key.pem indexb.html ec2-user@172.31.46.68:/var/www/html"
							}
					      }
 			    } 

		
			stage ('Slave-1') {
			     agent {
		              label {
		                      label "slave-1"
				                /* customWorkspace "/home/ec2-user/"  */
		                    }
		                } 
					steps {
						
						  sh "sudo chmod -R 777 /var/www/html"
						
						        sh "sudo mv /var/www/html/indexa.html /var/www/html/index.html"  
						
						
						  sh "sudo service httpd start"
					    } 
				
					
			       }
				  
			stage ('Slave-2'){
			     agent {
			
			           label {
				               label "lave-2"
					             /*customWorkspace "/home/ec2-user/"   */
			                 }
			              }
			      steps {
				       
						  sh "sudo chmod -R 777 /var/www/html"
						
						   sh "sudo mv /var/www/html/indexb.html /var/www/html/index.html"   
					   
				
						    sh "sudo service httpd start"
					    }
				
					 
				    }
			}	  
	}
 
