# STEPS to Deploy  Infra

1. Configure AWS CLI access on your System.

2. Configure CodeStarConnection to integrate your codepipeline with your Github account.

3. Push this code to your GITHUB repo.

4. Update Both **parameter.json** and **lambda-apig.json** file with your own values.

5. Deploy Resources By Createing stack in Cloudformation. Run Below command aand it will deploy Resources.

    ```
        aws cloudformation create-stack --stack-name test-air-stack --template-body file://infra-pipeline-deploy.yaml --parameters file://parameter.json --region us-west-1 --capabilities CAPABILITY_NAMED_IAM
    ```

6. Once above stack deployed Successfully. Go to Codepipeline console and you can see that pipeline already triggered. Pipeline will build and deploy Lambda function and apigateway.


	```
		curl --location --request POST 'http://<API-GAATEWAY ENDPOINT>/image' \
		--form 'file=@img.jpg' \
		--form 's3Key=img.jpg'
	```
