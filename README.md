# dummy-ghapp-deployer
<h1>
Deployer of Probot app on AWS Lambda 
</h1>

<body>
  <main>
    <section>
      <h2> Create the AWS Function </h2>
        <p>
          The first step of our code is to create the function by using the "create.yml" action. In order to use this action you have to set some secrets :
        </p>
        <dl>
          <dt> Information for the authentication </dt>
          <dd> AWS_ACCESS_KEY_ID : you can find this information inside the IAM Configuration </dd>
          <dd> AWS_SECRET_ACCESS_KEY : you can find this information inside the IAM Configuration </dd>
          <dd> AWS_REGION : region for the auth </dd>
          <dt> Function settings </dt>
          <dd> AWS_FUNCTION_ROLE : the role for your function, you can create a role inside the IAM configuration. </dd>
          <dd> LAMBDA_FUNCTION : this will be the name of your future function </dd>
          <dt> Values for the environmental variables </dt>
          <dd> AWS_GHAPP_ID : the github app id </dd>
          <dd> AWS_GHAPP_WEBHOOK_SECRET : the webhook secret </dd>
          <dd> AWS_GHAPP_PRIVATE_KEY : the private key of your application </dd>
          <dt> Configuration of the TRIGGER </dt>
          <dd> AWS_API_NAME : this will be the name of your http-api that will be used for the creation of the trigger </dd>
        </dl>
      <h3>Create the trigger</h3>
      <p>
          Once the create.yml execute all the jobs, the function will be created. The last step is to create a new 'Trigger'. 
      </p>
      <ol>
        <li> Log-in AWS </li>
        <li> Click on the search bar and type : Function. [in the voice LAMBDA] (after that you will see all the functions) </li>
        <li> Click on the function that you have just created, the name will be the same of your secret : LAMBDA_FUNCTION </li>
        <li> Go in the section : Configuration </li> 
        <li> Click on 'Triggers' </li>
        <li> Click on 'add trigger' </li>
        <li> Select an API-GATEWAY, click on 'Use existing API' and type the name of the API that you used in the secret : AWS_API_NAME, then 
        'Deployment stage' click on '$default' and thent in 'Security' select 'Open'. Click on add </li> 
      </ol>
        <h3>Attach the API-Gateway in to the GH Application </h3>
        <p>
            Once the API-Gateway is created, you have to copy the 'API endpoint' and put it inside your GitHub application's webhook_url
        </p>
      </ol>
    </section>
  </main>
</body>
  <!-- 
the role <strong>MUST</strong> have this policy name : AWSLambdaBasicExecutionRole-ef626d56-30a2-426d-a215-50f10b8781e3
-->
