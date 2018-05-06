"# dogIdentification" 

The last bit of codes creates the submission file in the proper format with the proper row ids and column names, yielding a
prediction column space for each id.

Looking over the poor performance of the model generalizing, and looking through the data, I can think of a few things that
are absolutely critical to making the model more effective. These include the following:

1) Using a bigger image size, preferably 256x256
    - this is limited by computing power and the resource. Using a 1.4 gb gpu was not sufficient for this project, requiring
        a migration to colab
    - this is expected to capture more defining curves of the dogs
2) Background blackout, due to confounding image colours
    - this is beyond my personal scope of ability. It first requires classifying the image in the background as the target
        using image recognition, then zeroing out all other pixels
    - I expect this to be the most important thing for this image, as in identifying dogs we need to use the full RGB spectrum,
        and looking at the images, our feature space for 123 target variables is severely hampered by the diversity of color 
        backgrounds.
3) More data
    - an obvious solution is image augmentation, but in this case, with 123 target variables 10,000 samples might not be truly
        enough, especially given the diversity of environments the photos were taken in. This can be circumvented using 
        solution #2, as I believe that to be the most important thing
4) Better model.
    - Without 1, 2, or 3, this will not alone give the best performance, but finer tuning can be performed once a cross validation
        goes above .1, which I managed to get on a single test.
5) GPU large enough to fit the data and model.
    - using a very small batch size is very bad. It was something I had to resort to due to small size of the available gpu components on           both my harddrive and in google colab.
       
"# Project Description"
Data Processing was done in jupyter notebook. Being limited by GPU on my personal machine, I used Colab to run the actual model training, then downloaded the weights file from Google Drive back down to my personal computer. At this point, I used Jupyter notebook again to run the model predictions and output generation.
