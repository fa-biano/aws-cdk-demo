# Welcome to your CDK TypeScript project

This is a blank project for CDK development with TypeScript.

The `cdk.json` file tells the CDK Toolkit how to execute your app.

## Useful commands

* `npm run build`   compile typescript to js
* `npm run watch`   watch for changes and compile
* `npm run test`    perform the jest unit tests
* `cdk deploy`      deploy this stack to your default AWS account/region
* `cdk diff`        compare deployed stack with current state
* `cdk synth`       emits the synthesized CloudFormation template

## Comandos utilizados e modificações

Para iniciar o projeto: `cdk init --language typescript`

No caminho `bin/aws-cdk-demo.ts` foi descomentada a linha 14 para automaticamente puxar as credenciais do AWS CLI: </br>
`env: { account: process.env.CDK_DEFAULT_ACCOUNT, region: process.env.CDK_DEFAULT_REGION }`

Instalado o modulo EC2: `npm install @aws-cdk/aws-ec2`

No caminho `lib/aws-cdk-demo-stack.ts` foi adicionado o codigo abaixo para criar um VPC (Virtual Private Cloud) utilizano o EC2:
  > import * as ec2 from 'aws-cdk-lib/aws-ec2'; </br>
  > </br>
  > constructor(scope: Construct, id: string, props?: cdk.StackProps) { </br>
  >   super(scope, id, props); </br>
  >   // We have created the VPC object from the VPC class </br>
  >   new ec2.Vpc(this, 'mainVPC', { </br>
  >     // This is where you can define how many AZs you want to use </br>
  >     maxAzs: 2, </br>
  >     // This is where you can define the subnet configuration per AZ </br>
  >     subnetConfiguration: [ </br>
  >        { </br>
  >          cidrMask: 24, </br>
  >          name: 'public-subnet', </br>
  >          subnetType: ec2.SubnetType.PUBLIC, </br>
  >        } </br>
  >     ] </br>
  >  }); </br>
  > }` </br>

  Testar a build: `npm run build`

  Realizar o deploy: `cdk deploy`

  O Deploy pode ser verificado no console AWS através do serviço Lambda.