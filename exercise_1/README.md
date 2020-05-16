## Deploy the S3 buckets

`aws cloudformation create-stack --region us-east-1 --stack-name c3-s3 --template-body file://exercise_1/c3-s3.yml`

Expected Output:

```
{
    "StackId": "arn:aws:cloudformation:us-east-1:4363053XXXXXX:stack/c3-s3/70dfd370-2118-11ea-aea4-12d607a4fd1c"
}
```
## Deploy VPC and Subnets

`aws cloudformation create-stack --region us-east-1 --stack-name c3-vpc --template-body file://exercise_1/c3-vpc.yml`

Expected Output:

```
{
    "StackId": "arn:aws:cloudformation:us-east-1:4363053XXXXXX:stack/c3-vpc/70dfd370-2118-11ea-aea4-12d607a4fd1c"
}
```

## Deploy Application Stack

`aws cloudformation create-stack --region us-east-1 --stack-name c3-app --template-body file://exercise_1/c3-app.yml --parameters ParameterKey=KeyPair,ParameterValue=<key pair name> --capabilities CAPABILITY_IAM
`

Expected Output:

```
{
    "StackId": "arn:aws:cloudformation:us-east-1:4363053XXXXXX:stack/c3-app/70dfd370-2118-11ea-aea4-12d607a4fd1c"
}
```

Expected example AWS Console status: https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks


## Uploading data to S3 buckets

`aws s3 cp free_recipe.txt s3://<BucketNameRecipesFree>/ --region us-east-1`
`aws s3 cp secret_recipe.txt s3://<BucketNameRecipesSecret>/ --region us-east-1`

## Test Application

`http://<ApplicationURL>/free_recipe`