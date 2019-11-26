# NLP-hw3


Introduction: This homework was about robust Phrasal chunking. Phrase chunking is a natural language process that separates and segments a sentence into its subconstituents, such as noun, verb, and prepositional phrases, abbreviated as NP, VP, and PP, respectively. The input data in dev and test files have been infected with noise so the input to our chunker has lots of spelling error which we have to handle in our code.
Based on baseline given in the instruction our steps to solve this problems are:    

- Create a one-hot vector v1 for the first character of the word.

- Create a vector v2 where the index of a character has the count of that character in the word.

- Create a one-hot vector v3 for the last character of the word.

- Combine the semi-Character RNN idea with the phrasal chunker from default.py:  

Concatenate to the word embedding input to the chunker RNN an input vector that is the character level             representation of the word.

And here is the code for this part: v1v2v3_list = []# Step 2.1 prepare additional dimensions
for w in sentence:

v1 = torch.zeros(100)
v2 = torch.zeros(100)
v3 = torch.zeros(100)
###### if w not in v1v2v3_list.keys():
v1[string.printable.index(w[0])] = 1
v3[string.printable.index(w[-1])] = 1
  for char in w:
     v2[string.printable.index(char)] += 1
v1v2v3_list.append(torch.cat((v1, v2, v3)))
V = torch.stack(v1v2v3_list) # len_stentence * 300
return V

