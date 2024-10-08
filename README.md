# Simple_Chatbot



In this notebook, I will be implementing my own version of the first ever Chatbot, ELIZA.

Background: ELIZA
The first ever Chatbot.
ELIZA Conversation
This Chatbot was released in 1966 (before the term Chatbot even existed) by Joseph Weizenbaum of MIT. This was a revolutionary program that allowed humans to converse with a computer. As you may have predicted, this was a retrieval-based system, very different from the "language models" of today. However, you may be surprised by how well it performed despite the simplicity of the system. Here is part of a conversation someone had with ELIZA, from the original paper (the capitalised sentences are ELIZA's responses):

Men are all alike.

IN WHAT WAY

They're always bugging us about something or other.

CAN YOU THINK OF A SPECIFIC EXAMPLE

Well, my boyfriend made me come here.

YOUR BOYFRIEND MADE YOU COME HERE

He says i'm depressed much of the time.

I AM SORRY TO HEAR YOU ARE DEPRESSED

It's true. I am unhappy.

DO YOU THINK COMING HERE WILL HELP YOU NOT TO BE UNHAPPY

......

The program used certain programmed rules to "transform" the input into the output. In order to do this, the program must first decompose the sentence based on certain criteria and then reassemble it based on the predefined assembly specifications. For example, if it is provided with the input sentence, "It seems that you hate me", it may be decomposed into:

1. It seems that
2. you
3. hate
4. me
   
Of these, (2) and (4) are recognised as key words. The program can then use the remaining sections of the sentence based on pre-defined rules to construct an output. For example, it may be programmed with the rule:

decomposition template:

(0 YOU 0 ME)

and the reassembly rule:

(WHAT MAKES YOU THINK I 3 YOU).

Here, the "0" represents any number of words, whereas the "3" represents the 3rd part of the sentence from before. Hopefully, this makes the implementation a little clearer. If not, don't worry as you'll understand how it works once you start implementing your own version!

For more details on the original ELIZA implementation, Click Here.

Specifications
As described above, my task will be to first read in a user string, then modify it to provide an output (sometimes subtly, sometimes drastically, depending on the input string).


The program should be able to handle all 1st and 2nd person pronouns, all 1st and 2nd person subject-verb pairs with the verb be and all possible forms of the verb. If it is unclear what is meant by this, you might want to do some googling.


An example is as follows:

Regular Expression: I am (.*)
Response: How long have you been %1?

Example Input that matches: I am sad.
Example Response: How long have you been sad?

Please note that this is a simplified version of the chatbot, and the original bot had a much more complex algorithm behind it.

There will be two tables to store all the logic of the bot: Reflection Table, Response Table


In the second part of the project, we will be giving the chatbot some emotional intelligence. This will be done by training a simple emotion classification model. We will then use this model to classify the sentiment of the user's input and respond accordingly.\
\
How our logic will work is as follows:
1. If there is a match in the response table, we will use the response from the table.
2. If there is no match, we will classify the emotion of the input and respond accordingly.

The model we will use is a simple Naive Bayes Classifier. This is a simple model that works well with text data. We will be using the `scikit-learn` library to train the model, and the huggingface `datasets` library to get the data.
