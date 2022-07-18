# Cyber-attacks-classification

Upon understanding how a deep learning network works and how it could be built, I started conducting ML analysis and building neural networks in hopes to classify the three types of cyber attacks, HTTP, TCP, and UDP. 

The first problem I encountered was due to the data being not properly cleaned -the loss was actually NAN. There were many potential root causes of this, but it was optimal to first check if the data set was properly cleaned. Using a quick for loop I found that the data set had na and inf values in the table, which made the calculation of the loss impossible. There were two ways to counter this. Since the NA values were concentrated in two feature columns, I could choose to drop all the features that had NAN or inf value. This was not advisable because the features could be very useful to the machine learning algorithm. Instead I dropped all the rows with these values since the data sample is so large, dropping a few rows should have a small impact. 


This is how I pre-processed my data - line 3 & 4 is where I deal with undefined values. The test data is also cleaned in this manner. 

After the data was cleaned, the machine learning algorithm managed to run. Since HTTP attacks make up a huge proportion  of the data set as there were very little tcp and udp attacks, the data set was essentially very biased. At first the accuracy was quite high, but it was dangerously deceiving. The algorithm essentially classified all the attacks to be HTTP. Since the data set was very biased, the loss still decreased but could not decrease beyond a further point. This was hard to identify simply through the accuracy and loss as they were deceiving. I identified this problem using the confusion matrix and a counting for loop. 

It was necessary to find a way to make the data set less biased. The ideal solution is to find more data/examples of tcp and udp attacks. Since that was not an available option, we simply duplicated the TCP and UDP dataset to offset the large amount of HTTP data. 


It was not enough to increase the number of TCP and UDP datasets, the model needed to be fine tuned by hyperparameters in order for the machine to learn. Other than changing the dataset, I have also adjusted the learning rate, batchsize, number of layers and number of nodes to optimize training

The results were much more reasonable than the previous test, as shown by the confusion matrix aforementioned. Using this model,I achieved an average loss of approx 0.5 and 90% accuracy. 

While the model was now considered trained, it was advised to examine accuracy through different metrix. I did this through calculating the false positive rate, false negative rate, true positive rate, and true negative rate of each class. 
