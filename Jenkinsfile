@Library('pipeline-framework')_
properties(
    [
        [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], 
        parameters(
             [
	        booleanParam(
                    defaultValue: false, 
                    description: 'Not Required for Production', 
                    name: 'QALAB'
                ),
				string(
                    defaultValue: '', 
                    description: '', 
                    name: 'CHECKOUT_USING_USER', 
                    trim: true
                ),
				string(
                    defaultValue: '', 
                    description: 'Not Required for Rancher', 
                    name: 'OCLOGIN_USING_USER', 
                    trim: true
                ),
                string(
                    defaultValue: '', 
                    description: 'Default will be used if not provided', 
                    name: 'DEVOPS_REPO', 
                    trim: true
                ),
                string(
                    defaultValue: '', 
                    description: 'Default will be used if not provided', 
                    name: 'ENVIONMENTS_REPO', 
                    trim: true
                ),				 
                string(
                    defaultValue: '20.08.01', 
                    description: '', 
                    name: 'CURRENT_BRANCH',
                    trim: true
                ),
                string(
                    defaultValue: '', 
                    description: '', 
                    name: 'AGENT', 
                    trim: true
                ),
				string(
                    defaultValue: '', 
                    description: '', 
                    name: 'DATACENTER', 
                    trim: true
                ),
				string(
                    defaultValue: '', 
                    description: '', 
                    name: 'CUSTOMER', 
                    trim: true
                ),
				string(
					defaultValue: 'serviceaccount_kubeconfig', 
					description: '', name: 'KUBECONFIG_CREDENTIAL', 
					trim: true
					),
				string(
                    defaultValue: '', 
                    description: '', 
                    name: 'ENVIRONMENT', 
                    trim: true
                ),
				string(
                    defaultValue: '', 
                    description: '', 
                    name: '__OC_LOGIN_URL__', 
                    trim: true
                ),
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: '__K8_DEPLOYMENT__'
                ),												
                string(
                    defaultValue: '', 
                    description: '', 
                    name: '__TENANT_ID__'
                ), 
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'DNS_REGISTRATION'
                ), 
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'CREATE_TENANT_INNOVATION_SUITE'
                ), 
				booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'SETUP_SR_FUNCTIONAL_ROLE'
                ), 
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'CREATE_ROUTES'
                ), 
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'EMAIL_CONFIGURATION'
                ), 
                booleanParam(
                    defaultValue: true, 
                    description: 'For Chatbot Customer', 
                    name: 'BLUEMIX_CONVERSATION'
                ), 
                booleanParam(
                    defaultValue: true, 
                    description: 'For Cognitive Automation Customer', 
                    name: 'BLUEMIX_NLC'
                ), 
                booleanParam(
                    defaultValue: true, 
                    description: 'For Cognitive Automation Customer', 
                    name: 'BLUEMIX_TONEANALYZER'
                ), 
                booleanParam(
                    defaultValue: true, 
                    description: 'For Cognitive Automation Customer', 
                    name: 'ENABLE_SUMMARIZATION'			
				),	
                booleanParam(
                    defaultValue: true, 
                    description: 'For Cognitive Search Customer', 
                    name: 'BLUEMIX_DISCOVERY'
                ), 				
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'BWF_LICENSE'
                ), 
				booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'BWF_CATALOG_CONFIG'
                ), 
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'MCSM_LICENSE'
                ),
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'SYNTH_MON_DATA_LOAD'
                ),
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'CHATBOT_RSSO_CONFIGURATION'
                ),
				booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'CHATBOT_DWP_CONFIGURATION'
                ),
				booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'CHATBOT_DWPC_CONFIGURATION'
                ),
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'CHATBOT_VIRTUALCHAT_CONFIGURATION'
                ),
                booleanParam(
                    defaultValue: true, 
                    description: '', 
                    name: 'UPDATE_DEVOPS_APP'
                ),
                password( 
                    description: '', 
                    name: '__ISUITE_SAAS_ADMIN_PASSWORD__'
                ),
                password( 
                    description: '', 
                    name: '__TENANT_ADMIN_USER_PASSWORD__'
                ),
                password( 
                    description: '', 
                    name: '__TENANT_DATABASE_USER_PASSWORD__'
				),
                password( 
                    description: '', 
                    name: '__EMAIL_SERVER_USER_PASSWORD__'
                ),
                password( 
                    description: '', 
                    name: '__RSSO_ADMIN_PASSWORD__'
                ),
                password( 
                    description: '', 
                    name: '__DWP_CATALOG_PASSWORD__'
                ),	
                password( 
                    description: '', 
                    name: '__DWP_PASSWORD__'
                ),
                password( 
                    description: '', 
                    name: '__VIRTUAL_CHAT_PASSWORD__'
				),	
				password( 
                    description: '', 
                    name: '__REMEDY_ADMIN_PASSWORD__'
				),																	
                password( 
                    description: '', 
                    name: '__PGPASSWORD__'
                ),
				string(
                    defaultValue: '', 
                    description: '', 
                    name: 'NOTIFYLIST', 
                    trim: true
                )
            ]
        )
    ]
)
def DEVOPS_NOTIFICATION_REVIEWERS = "Nikhil_Shah@bmc.com,Devendra_Yadav@bmc.com,Satbachan_Singh@bmc.com"
if ("${QALAB}" == "false" && "${NOTIFYLIST}" != '') {
 NOTIFYLIST = "${NOTIFYLIST}" + "," + "${DEVOPS_NOTIFICATION_REVIEWERS}"
} else if ("${QALAB}" == "false" && "${NOTIFYLIST}" == '') {
 NOTIFYLIST = "${DEVOPS_NOTIFICATION_REVIEWERS}"
}

timeout(360){
setDeaultProperties("${QALAB}")
def ASSIGNED_AGENT=getAssignedAgent("${QALAB}")
node("${ASSIGNED_AGENT}"){
		try{
				setPipelineProperties()
                startStage("${PIPELINE_NAME}","${PIPELINE_TYPE}");
    			checkoutDevopsRepos();
				echo "##################################################################################################"
				stage('Print Image Version'){
					sh'''
						set +x
						. ${WORKSPACE}/pipeline/vars/common-environment.vars
						cp ${WORKSPACE}/environments/${DATACENTER}/${CUSTOMER}/is/${ENVIRONMENT}/common-dynamic-environment.vars ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
						cp ${WORKSPACE}/environments/${DATACENTER}/dc-common.vars ${DC_COMMON_VARIABLE_FILE}
	                    cp ${WORKSPACE}/environments/${DATACENTER}/${CUSTOMER}/is/${ENVIRONMENT}/tenant/${__TENANT_ID__}/is-tenant.vars ${TENANT_VARIABLE_FILE}
						cp ${WORKSPACE}/environments/${DATACENTER}/${CUSTOMER}/is/${ENVIRONMENT}/is-db-environment.vars ${IS_DB_ENV_VARIABLE_FILE}
						cp ${WORKSPACE}/environments/${DATACENTER}/${CUSTOMER}/is/${ENVIRONMENT}/bundles-environment.vars ${BUNDLES_ENV_VARIABLE_FILE}
						bash ${PRINT_IMAGE_VERSION} ${IS_FS_ENV_VARIABLE_FILE} ${BUNDLES_ENV_VARIABLE_FILE} ${IS_DB_ENV_VARIABLE_FILE} ${TENANT_VARIABLE_FILE} ${DC_COMMON_VARIABLE_FILE}
					'''
				}
				connectClusters("${DATACENTER}", "${KUBECONFIG_CREDENTIAL}")
				currentBuild.displayName="${__TENANT_ID__}-${DATACENTER}-${CUSTOMER}-${ENVIRONMENT}-${env.BUILD_NUMBER}"
				echo "##################################################################################################"
				stage('DNS Registration'){
					if("$DNS_REGISTRATION" == "true"){						
						try{
							sh'''
							set +x
							echo "Registring internal and external DNS for tenant"
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							export __DNS_NOTIFY_LIST__="${USER}@bmc.com"
							echo "Starting DNS Registration with parameter 3"
							bash ${ACTIVATION_MASTER} 3
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "DNS Registration failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.DNS_REGISTRATION is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Innovation Suite Tenant Creation'){
					if("$CREATE_TENANT_INNOVATION_SUITE" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${IS_DB_ENV_VARIABLE_FILE}
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Creating of Innovation Suite Tenant "	
							echo "Starting Innovation Suite Activation ${ACTIVATION_MASTER} with parameter 1"
							bash ${ACTIVATION_MASTER} 1
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "Tenant Creation failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.Tenant_Creation_for_Innovation_suite is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Setup SR Functional Role'){
					if("$SETUP_SR_FUNCTIONAL_ROLE" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${IS_DB_ENV_VARIABLE_FILE}
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Setup SR Functional Role"	
							echo "Setup SR Functional Role ${ACTIVATION_MASTER} with parameter 20"
							bash ${ACTIVATION_MASTER} 20
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "Setup SR Functional Role failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.SETUP_SR_FUNCTIONAL_ROLE is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Route or Ingress Creation'){
					if("$CREATE_ROUTES" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Creating Routes/Ingress"	
							echo "Starting Route creation ${ACTIVATION_MASTER} with parameter 2"
							bash ${ACTIVATION_MASTER} 2
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "Route Creation failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.Route_Creation is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Innovation Suite Email Config'){
					if("$EMAIL_CONFIGURATION" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							. ${DC_COMMON_VARIABLE_FILE}
	                        . ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
	                        DC=`echo ${DATACENTER} | awk -F'-' '{print $1}'`
							MAILBOX=`echo "MAILBOX-${DC}-${__TENANT_ID__}-${ENVIRONMENT}" | tr '[:lower:]' '[:upper:]'`
							export __MAILBOX_NAME__=${MAILBOX}
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008" )
	                        bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
	                        bash ${GENERATE_VARS_FROM_ENV_SHELL} ${DC_COMMON_VARIABLE_FILE}
	                        bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							echo "Email Configuration"	
							echo "Starting Email Configuration ${ACTIVATION_MASTER} with parameter 4"
							bash ${ACTIVATION_MASTER} 4
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "Email Configuration failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.Email_Configuration is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Watson Chatbot Config'){
					if("$BLUEMIX_CONVERSATION" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
							export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting Bluemix configuration - ${ACTIVATION_MASTER} with parameter 5"
							bash ${ACTIVATION_MASTER} 5
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "Bluemix configuration failed for CONVERSATION Service"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.BLUEMIX_CONVERSATION is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Watson NLC Config'){
					if("$BLUEMIX_NLC" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
							export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting Bluemix configuration - ${ACTIVATION_MASTER} with parameter 12"
							bash ${ACTIVATION_MASTER} 12
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "Bluemix configuration failed for NLC Service"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.BLUEMIX_NLC is set for FALSE"
					}
				}
				echo "##################################################################################################"				
				stage('Watson Toneanalyzer Config'){
					if("$BLUEMIX_TONEANALYZER" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
                            				export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting Bluemix configuration - ${ACTIVATION_MASTER} with parameter 15"
							bash ${ACTIVATION_MASTER} 15
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "Bluemix configuration failed for TONEANALYZER Service"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.BLUEMIX_TONEANALYZER is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Summarization Config'){
					if("$ENABLE_SUMMARIZATION" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
                            if [ "${ENVIRONMENT}" == "prod" ]; then
	                            export __ENV_URI__=""
                            else
	                            export __ENV_URI__="${__ENV__}-"
                            fi
							export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008" )
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting Summarization configuration - ${ACTIVATION_MASTER} with parameter 16"
							bash ${ACTIVATION_MASTER} 16
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "SUMMARIZATION Configuration Failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.ENABLE_SUMMARIZATION is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Watson Discovery Config'){
					if("$BLUEMIX_DISCOVERY" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
							export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting Bluemix configuration - ${ACTIVATION_MASTER} with parameter 13"
							bash ${ACTIVATION_MASTER} 13
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "Bluemix configuration failed for DISCOVERY Service"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.BLUEMIX_DISCOVERY is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Assign BWF License'){
					if("$BWF_LICENSE" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting BWF license Activation: ${ACTIVATION_MASTER} with parameter 6"
							bash ${ACTIVATION_MASTER} 6
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "BWF Licensing failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.BWF_LICENSE is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('BWF-Catalog Config'){
					if("$BWF_CATALOG_CONFIG" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting BWF Catalog config : ${ACTIVATION_MASTER} with parameter 18"
							bash ${ACTIVATION_MASTER} 18
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "BWF Catalog Config failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.BWF_CATALOG_CONFIG is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Assign MCSM License'){
					if("$MCSM_LICENSE" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting MCSM license Activation: ${ACTIVATION_MASTER} with parameter 7"
							bash ${ACTIVATION_MASTER} 7
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "MCSM Licensing failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.MCSM_LICENSE is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Synthetic Monitoring Data Load'){
					if("$SYNTH_MON_DATA_LOAD" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting Synthetic Monitoring Data Load: ${ACTIVATION_MASTER} with parameter 8"
							bash ${ACTIVATION_MASTER} 8
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "!! ERROR: Synthetic Monitoring Data Load Failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.SYNTH_MON_DATA_LOAD is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Chatbot RSSO Config'){
					if("$CHATBOT_RSSO_CONFIGURATION" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting Chatbot RSSO Configuration: ${ACTIVATION_MASTER} with parameter 9"
							bash ${ACTIVATION_MASTER} 9
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "!! ERROR: Chatbot RSSO Configuration Failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.CHATBOT_RSSO_CONFIGURATION is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Chatbot DWP Config'){
					if("$CHATBOT_DWP_CONFIGURATION" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting DWP Configuration: ${ACTIVATION_MASTER} with parameter 10"
							bash ${ACTIVATION_MASTER} 10
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "!! ERROR: Chatbot DWP Configuration Failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.CHATBOT_DWP_CONFIGURATION is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Chatbot Catalog Config'){
					if("$CHATBOT_DWPC_CONFIGURATION" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting DWPC Configuration: ${ACTIVATION_MASTER} with parameter 11"
							bash ${ACTIVATION_MASTER} 11
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "!! ERROR: Chatbot DWPC Configuration Failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.CHATBOT_DWPC_CONFIGURATION is set for FALSE"
					}
				}
				echo "##################################################################################################"
				stage('Chatbot Virtualchat Config'){
					if("$CHATBOT_VIRTUALCHAT_CONFIGURATION" == "true"){						
						try{
							sh'''
							set +x
							. ${WORKSPACE}/pipeline/vars/common-environment.vars
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${COMMON_DYNAMIC_ENV_VARIABLE_FILE}
							. ${WORKSPACE}/pipeline/tasks/loadenv.sh
              	            export __IS_CLUSTER_IP__=$(bash ${GET_CLUSTERIP} ${DEPLOYMENT_COMMAND} ${__K8_NAMESPACE__} "is-sg" "8008")
							bash ${GENERATE_VARS_FROM_ENV_SHELL} ${TENANT_VARIABLE_FILE}
							echo "Starting Virtualchat Configuration: ${ACTIVATION_MASTER} with parameter 17"
							bash ${ACTIVATION_MASTER} 17
							'''	
						}catch(Exception e){
							currentBuild.result = 'FAILURE'
							echo "!! ERROR: Chatbot Virtualchat Configuration Failed"
							throw e
						}
					}
					else
					{
						echo "Skipping Stage.CHATBOT_VIRTUALCHAT_CONFIGURATION is set for FALSE"
					}
				}
	      echo "##################################################################################################"
		  endStage("${PIPELINE_NAME}","${PIPELINE_TYPE}")
			}
			catch(Exception e){
				currentBuild.result = 'FAILURE'
			}
			finally{
				clearKubeconfig()
				zipLogs("${env.LOG_FILE}","${env.LOG_DIR}");
				env.NOTIFICATION_SUBJECT="[${__TENANT_ID__}] ${PIPELINE_NAME} ${PIPELINE_TYPE} ${DATACENTER}-${CUSTOMER}-${ENVIRONMENT}-${CURRENT_BRANCH} activity status: ${currentBuild.currentResult}"
				sendEmail("${env.NOTIFICATION_SUBJECT}","${NOTIFYLIST}","${env.LOG_FILE_NAME}");

			}
			failFast: true
	}
}
def setPipelineProperties()
{
	env.LOG_DIR="${env.WORKSPACE}/activation/logs/"
    env.LOG_FILE="${env.WORKSPACE}/activation-logs.zip"
	env.LOG_FILE_NAME="activation-logs.zip"
	env.PIPELINE_TYPE="activation"
	env.PIPELINE_NAME="Innovation suite"
}
