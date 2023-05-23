---
title: Updating the GPT-4 PDF Chatbot LangChain Repository (mayooear)
summary: Changes to gpt4-pdf-chatbot-langchain
tags:
  - LangChain
date: '2023-05-19T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  caption: Credit to mayooear
  focal_point: Smart

links:
  - icon: github
    icon_pack: fab
    name: mayooear
    url: https://github.com/mayooear/gpt4-pdf-chatbot-langchain
url_code: ''
url_pdf: ''
url_slides: ''
url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
# slides: example

---

The GPT-4 PDF Chatbot LangChain repository is a powerful tool that uses the GPT-4 API to build a chatGPT chatbot for multiple large PDF files. It leverages technologies like LangChain, Pinecone, TypeScript, OpenAI, and Next.js to achieve this. LangChain is a framework that makes it easier to build scalable AI/LLM apps and chatbots, while Pinecone serves as a vector store for storing embeddings and your PDF in text to later retrieve similar doc

However, we're going to make some changes to the repository. We'll be removing Pinecone and updating it to Faiss. Here's how you can do that:

1. **Install Faiss Node**
   Run `npm install faiss-node@0.1.1` to add Faiss Node to your project.

2. **Update /scripts/ingest-data.ts**
   Replace the Pinecone lines with:
   ```javascript
   import { FaissStore } from "langchain/vectorstores/faiss";
   ```
   And update the document loading process as follows:
   ```javascript
   // Load the docs into the vector store
   const vectorStore = await FaissStore.fromDocuments(
     docs,
     new OpenAIEmbeddings()
   );

   await vectorStore.save('./index');
   ```

3. **Update utils/makechain.ts**
   Replace the Pinecone lines with:
   ```javascript
   import { FaissStore } from "langchain/vectorstores/faiss";
   ```
   And update the chain creation process as follows:
   ```javascript
   export const makeChainFaiss = (vectorstore: FaissStore) => {
     const model = new OpenAI({
       temperature: 0, // increase temepreature to get more creative answers
       modelName: 'gpt-3.5-turbo', //change this to gpt-4 if you have access
     });

     const chain = ConversationalRetrievalQAChain.fromLLM(
       model,
       vectorstore.asRetriever(),
       {
         qaTemplate: QA_PROMPT,
         questionGeneratorTemplate: CONDENSE_PROMPT,
         returnSourceDocuments: true, //The number of source documents returned is 4 by default
       },
     );
     return chain;
   };
   ```

4. **Update pages/api/chat.ts**
   Replace the Pinecone lines with:
   ```javascript
   import { makeChain, makeChainFaiss } from '@/utils/makechain';
   import { FaissStore } from "langchain/vectorstores/faiss";
   ```
   And add the following to load the vector store and create the chain:
   ```javascript
   // Load the vector store from the same directory
   const loadedVectorStore = await FaissStore.load(
     './index',
     new OpenAIEmbeddings()
   );

   //create chain
   const chainFaiss = makeChainFaiss(loadedVectorStore);

   //Ask a question using chat history
   const response = await chainFaiss.call({
     question: sanitizedQuestion,
     chat_history: history || [],
   });
   ```

5. ***Set up your .env file***
You will need to add your Azure OpenAI Service details to your .env file. This should include your Azure OpenAI API Key, instance name, deployment name, completions deployment name, embeddings deployment name, and API version. The entries in your .env file should look something like this:

    ```
    AZURE_OPENAI_API_KEY="..."
    AZURE_OPENAI_API_INSTANCE_NAME="..."
    AZURE_OPENAI_API_DEPLOYMENT_NAME="..."
    AZURE_OPENAI_API_COMPLETIONS_DEPLOYMENT_NAME="..."
    AZURE_OPENAI_API_EMBEDDINGS_DEPLOYMENT_NAME="..."
    AZURE_OPENAI_API_VERSION="..."
    ```
---
This should complete the update of your GPT-4 PDF Chatbot LangChain repository to use Faiss instead of Pinecone.
