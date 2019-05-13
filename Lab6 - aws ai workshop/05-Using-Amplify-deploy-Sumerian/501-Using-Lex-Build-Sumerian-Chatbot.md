Using Amazon Lex to Build a Sumerian Chatbot
========================

Amazon Lex is a service for building conversational interfaces into any application using voice and text. As a fully managed service, you don’t need to worry about managing infrastructure. 

Amazon Sumerian lets you create and run virtual reality (VR), augmented reality (AR), and 3D applications quickly and easily without requiring any specialized programming or 3D graphics expertise.

## About this Lab
### Scenario

In this lab we will use an example Amazon Lex bot and connect it with a Sumerian host using the state machine and dialogue component.

<center>
<img src="./images/501-0.png" alt="501-0.png" width="70%">
</center>

 ## Prerequisites
  -  Make sure you are in __US East (N. Virginia)__, which short name is __us-east-1__.

## Lab tutorial
### Create an Amazon Cognito Identity Pool

Before we create the Sumerian scene, we need to set up an AWS CloudFormation stack.

- Create [AWS CloudFormation stack template](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https:%2F%2Fs3.amazonaws.com%2Fsumerian-cfn-templates%2FLexPollyExampleTemplate.yml&stackName=AmazonSumerianLexPollyTutorialStack) with this link.

> You may choose the "new AWS CloudFormation console" to complete this step.

- Check __I acknowledge that AWS CloudFormation might create IAM resources__, and __Create stack__.

<center>
<img src="./images/501-001-CloudFormation_create-01.jpg" alt="501-001-CloudFormation_create-01.jpg" width="70%">
</center>

- Be sure the __Stack status__ is __CREATE_COMPLETE__.

> NOTES : It will take a few minutes to create.

<center>
<img src="./images/501-002-CloudFormation_status-01.jpg" alt="501-002-CloudFormation_status-01.jpg" width="70%">
</center>

- Click __Outputs__ on panel, copy the __CognitoIdentityPoolID__, you will enter this value in Sumerian.
<center>
<img src="./images/501-003-CloudFormation_copy url-01.jpg" alt="501-003-CloudFormation_copy url-01.jpg" width="70%">
</center>

### Create an Amazon Lex Chatbot 
We use Amazon Lex template provided in this tutorial.
- On the __Service__ menu, click __Amazon Lex__, choose __Create__.

- Choose __BookTrip__ template, type __Bot name__ : `yourbotname`.

<center>
<img src="./images/501-004-Amazon Lex_create-01.jpg" alt="501-004-Amazon Lex_create-01.jpg" width="70%">
</center>

- __COPPA__ click __NO__, and __Create__.

<center>
<img src="./images/501-005-Amazon Lex_create-02.jpg" alt="501-005-Amazon Lex_create-02.jpg" width="70%">
</center>

- Choose the bot created before, click __Settings__, choose __Aliases__.

    __Alias name__ : `test`

    __Bot version__ : `Latest`

- Click __PLUS__ icon to add a new alias.

<center>
<img src="./images/501-006-Lex Chatbox_publish-01.jpg" alt="501-006-Lex Chatbox_publish-01.jpg" width="70%">
</center>

- Click __Publish__.
- __Choose an alias__ : `test `, and __Publish__.

<center>
<img src="./images/501-007-Lex Chatbox_publish-02.jpg" alt="501-007-Lex Chatbox_publish-02.jpg" width="70%">
</center>

> Waiting for publish, and you can close the page. 

### Create an Amazon Sumerian Scene 

- On the __Service__ menu, click __Amazon Sumerian__, you will get into the __Amazon Sumerian Dashboard__.



- Click __Create new scene__, and type your __Scene name__.

- Click the Entities of __yourscenename__ on the upper left corner, and then extend the __AWS Configuration__ on the right side.

- Insert your __CognitoIdentityPoolID__ into the __AWS configuration__ component.

<center>
<img src="./images/501-008-Sumerian_insert poolID-01.jpg" alt="501-008-Sumerian_insert poolID-01.jpg" width="50%">
</center>

- Click __Import Assets__, choose __Maya__ and select __Add__ to add a host.

<center>
<img src="./images/501-009-Sumerian_import asset-01.jpg" alt="501-009-Sumerian_import asset-01.jpg" width="70%">
</center>


- __Maya__ will show in the __Assets__ on your left side.

<center>
<img src="./images/501-010-Sumerian_import asset-02.jpg" alt="501-010-Sumerian_import asset-02.jpg" >
</center>

- Drop the __Maya__ in your scene, you will see __Maya__.

<center>
<img src="./images/501-011-Sumerian_import asset-03.jpg" alt="501-011-Sumerian_import asset-03.jpg" width="50%">
</center>

> Note : You may need to zoom in to see Maya.

<center>
<img src="./images/501-012-Sumerian_import asset-04.jpg" alt="501-012-Sumerian_import asset-04.jpg" width="50%">
</center>

### Adding the Dialogue Component
- Select __Maya__ entities, and click __Add component__, choose __Dialogue__.

<center>
<img src="./images/501-013-Sumerian_add component-01.jpg" alt="501-013-Sumerian_add component-01.jpg">
</center>

- Insert the values for __Name__ and __Alias__, these inputs reference the Amazon Lex chatbot what you created.
<center>
<img src="./images/501-014-Sumerian_add dialogue-01.jpg" alt="501-014-Sumerian_add dialogue-01.jpg">
</center>

### Creating a Chatbot Behavior Using the State Machine

- Select __Maya__ entities, and click __Add component__, choose __State Machine__.

<center>
<img src="./images/501-015-Sumerian_add component-02.jpg" alt="501-015-Sumerian_add component-02.jpg">
</center>

- Open the __State Machine__, click __PLUS__ button to add a new behavior.

<center>
<img src="./images/501-016-Sumerian_add behavior-01.jpg" alt="501-016-Sumerian_add behavior-01.jpg">
</center>

- Rename the __name__ : `ChatBot`.

<center>
<img src="./images/501-017-Sumerian_name chatbox-01.jpg" alt="501-017-Sumerian_name chatbox-01.jpg">
</center>

- Rename __State 1__ : `Start`, and choose __Add Action__.

<center>
<img src="./images/501-018-Sumerian_add action-01.jpg" alt="501-018-Sumerian_add action-01.jpg">
</center>

- Search for and __add__ `AWS SDK Ready`.

<center>
<img src="./images/501-019-Sumerian_add action-02.jpg" alt="501-019-Sumerian_add action-02.jpg" width="50%">
</center>

- Click __Add State__ for __five__ times to create five states.

<center>
<img src="./images/501-020-Sumerian_add state-01.jpg" alt="501-020-Sumerian_add state-01.jpg" width="50%">
</center>


> It will be like this.

<center>
<img src="./images/501-021-Sumerian_add state-02.jpg" alt="501-021-Sumerian_add state-02.jpg" width="50%">
</center>

-  Choose the new state, and __rename__ it.

    __State 1__ : `Wait for Input`

    __State 2__ : `Start Recording`

    __State 3__ : `Stop Recording`

    __State 4__ : `Process with Lex`

    __State 5__ : `Play Response`

<center>
<img src="./images/501-022-Sumerian_rename state-01.jpg" alt="501-022-Sumerian_rename state-01.jpg" width="70%">
</center>

- Click state __Wait for Input__, add a __Key Down__ action.

<center>
<img src="./images/501-023-Sumerian_add action-03.jpg" alt="501-023-Sumerian_add action-03.jpg" width="70%">
</center>

- Change the key : __T__

<center>
<img src="./images/501-024-Sumerian_add action-04.jpg" alt="501-024-Sumerian_add action-04.jpg">
</center>

- Click state __Start Recording__, add  __Start Microphone Recording__ and __Key Up__ action.

<center>
<img src="./images/501-025-Sumerian_add action-05.jpg" alt="501-025-Sumerian_add action-05.jpg">
</center>

- Click state __Stop Recording__, add a __Stop Microphone Recording__ action.

<center>
<img src="./images/501-026-Sumerian_add action-06.jpg" alt="501-026-Sumerian_add action-06.jpg">
</center>

- Click state __Process with Lex__, add a __Send Audio Input to Dialogue Bot__ action.

<center>
<img src="./images/501-027-Sumerian_add action-07.jpg" alt="501-027-Sumerian_add action-07.jpg">
</center>

> Do not select Log user input or Log bot response.

- Click state __Play Response__, add a __Start Speech__ action and select __Use Lex Response__.

<center>
<img src="./images/501-028-Sumerian_add action-08.jpg" alt="501-028-Sumerian_add action-08.jpg">
</center>

- Adding transitions by __clicking__ the state and __dragging__ the arrow to another state

> On the Process With Lex state, drag the transition from the "On Response Ready output".

<center>
<img src="./images/501-029-Sumerian_add action-09.jpg" alt="501-029-Sumerian_add action-09.jpg" width="70%">
</center>

> The final graph will look like the following.

<center>
<img src="./images/501-030-Sumerian_add action-010.jpg" alt="501-030-Sumerian_add action-010.jpg" width="70%">
</center>

### Publish Sumerian Chatbot

- Click __Publish__, select __Create publish link__, and then __Publish__.

<center>
<img src="./images/501-031-Sumerian_publish-01.jpg" alt="501-031-Sumerian_publish-01.jpg" >
</center>

- __Copy__ the link.

<center>
<img src="./images/501-032-Sumerian_publish-02.jpg" alt="501-032-Sumerian_publish-02.jpg">
</center>

- __Paste the link__ on your browser, you can press __T__ to talk with her.

> You can say "Book a hotel" or "Book a car" to start the dialogue.

<center>
<img src="./images/501-033-Sumerian_publish-03.jpg" alt="501-033-Sumerian_publish-03.jpg">
</center>

## Conclusion
Congratulations! We now have learned how to:
- Create an Amazon Cognito Identity Pool
- Create an Amazon Lex chatbot
- Create an Amazon Sumerian Scene

## Next Level:
- [Using-Amplify-Deploy-Sumerian-with-React](../05-Using-Amplify-deploy-Sumerian/502-Using-Amplify-Deploy-Sumerian-with-React.md)