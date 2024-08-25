# sn-togetherai-tools
An easily configurable collection of generative AI tools for ServiceNow that utilizes Together.AI's serverless endpoints for GenAI tasks. 

## Together AI - Run AI with an API

1. [https://together.ai](https://www.together.ai/)
2. Sign in with Github
3. Get your API key - [https://api.together.xyz/settings/api-keys](https://api.together.xyz/settings/api-keys)

Together.ai provides $5.00 worth of free credits for each account, and I've found with their optimizations discussed [here](https://www.together.ai/blog/together-inference-engine-v1), this is a decent amount of credits to get started with.

## ServiceNow

1. Download and import the update set xml.
2. Navigate to Together AI > Together AI Properties in the filter navigator.
3. Add your Together.ai API key to the x_690795_together.togetherai_api_key System Property.
4. Modify the model values for each of the gen AI utilities if you wish. By default, the Knowlege and Code generation utilities use the meta-llama/Meta-Llama-3.1-405B-Instruct-Turbo model and the Incident Summarization utility uses meta-llama/Meta-Llama-3.1-70B-Instruct-Turbo. Please note: I've defaulted the code and knowledge generation models to a model that can be quite expensive to run compared to other models. This is to show the accuracy with which the models can perform those functions. Please change to another model from the list of 'Chat' models if you wish to reduce token usage/cost in favor of less precise outputs.

## Simple model testing
1. If you wish to quickly test a model, open the Together.AI Subflow.
2. Click "Test".
3. Enter a model and prompt. Note: The list of models can be found at [https://api.together.xyz/models](https://api.together.xyz/models) and you will need to enter the full model string including author and model name. (The default in subflow is meta-llama/Meta-Llama-3.1-405B-Instruct-Turbo)

**Note: Embedding and Image generation model types are currently not supported. Chat models are supported by default. If you need to test a language model, please update the subflow's resource path input to '/v1/completions'**

![image](https://github.com/user-attachments/assets/18d0189a-5c14-4662-a972-575b9a114852)

## Code Generation
1. To test the code generation capability, create a new record of one of the following types: Client Script, Catalog Client Script, Fix Script, Business Rule, UI Action, or Script Include.
2. In the new record creation, there is a Generate Code button in the top right corner of the form.
3. Click the Generate Code button, enter a code generation prompt, and click Generate Code.
4. Clicking the button in the UI page/Modal makes a call a Script Include (togetherAIUtils), which uses the generate_code POST method of the Together.AI REST message to send the prompt to the Together AI LLM endpoint. The response is returned and displayed in the UI page/Modal and can be copied to the clipboard using the Copy button.
![image](https://github.com/user-attachments/assets/fbc862a9-ab67-4650-94f4-1f8fc3af053c)

## Incident Summarization
1. To test the Incident Summarization capability, open an existing incident record or creat a new one.
2. Click the Summarize Incident button.
3. In the UI Page/Modal, click Summarize.
4. Clicking the button in the UI page/Modal makes a call a Script Include (togetherAIUtils), which uses the summarize POST method of the Together.AI REST message to send the prompt to the Together AI LLM endpoint. The response is returned and displayed in the UI page/Modal and can be copied to the clipboard using the Copy button.
![incident-summarize-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/e952ed35-eeea-44da-9d51-f865b0704e89)


## Knowledge Article Generation
1. To test the Knowledge Generation capability, open an existing knowledge article or create a new one.
2. On the knowlede article record form, click Generate Knowledge.
3. In the UI Page/Modal, click Generate Knowledge.
4. Clicking the button in the UI page/Modal makes a call a Script Include (togetherAIUtils), which uses the generate_knowledge POST method of the Together.AI REST message to send the prompt to the Together AI LLM endpoint. The response is returned and displayed in the UI page/Modal and can be copied to the clipboard using the Copy button.
![knowledge-generation-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/2ff664aa-89fb-4b9b-81e6-ddb692bcf9eb)

## Usecase

Since ServiceNow's Now Assist product is unavailable in PDIs, this allows for testing of GenAI responses using together.ai's library of serverless endpoint models. Note that this application is primarily for testing or demonstration purposes. I cannot guarantee you won't encounter any bugs, and the application is provided as-is without support. Though, I will be happy to answer any questions and would love feedback. Just send me a DM on Linkedin. https://www.linkedin.com/in/kyleburnswi/

## Future plans
* Task summarization
* CSM Case Summarization
* Virtual Agent Integration
* + More TBD
