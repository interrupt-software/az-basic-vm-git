Name
	./create_var.bash

Description
	
Makes an API call to your Terraform Enterprise, or Terraform Cloud
environment to create a variable in a workspace. This script assumes
that the pipeline process is able to access the following variables:

	TFE HOST: Where Terraform Enterprise or Terraform Cloud is hosted.
	TFE ORG: Your TFE/C organization.
	TFE_TOKEN: Your personal access TFE/C token.
	TFE_WORKSPACE: The desired workspace in your TFE/C organization.

Arguments
	<name> <value> [env | terraform] [true | false]

	NAME: Name of the variable
	VALUE: Value of the variable
	CAT: Category for the variable; either "env" or "terraform". Defaults to "env".
	SENSITIVE: Visibility for the variable; either "true" or "false". Defaults to "true".

Example:
	./create_var.bash ARM_CLIENT_SECRET $ARM_CLIENT_SECRET env true
	./create_var.bash public_key $"{PUBLIC_KEY}" terraform


for var in ARM_CLIENT_ID ARM_CLIENT_SECRET ARM_SUBSCRIPTION_ID ARM_TENANT_ID
do
./create_var.bash $var $(printenv $var) env true
done

./create_var.bash public_key $"{PUBLIC_KEY}" terraform

