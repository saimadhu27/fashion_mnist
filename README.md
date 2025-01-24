## Fashion_mnist

This repo contains the code for the fashion MNIST dataset.

Some questions that popped in my mind when I started working with CNN<br>
- Input_shape of images like image width and height?<br>
ans: If the image is greyscale then we have 1 colour channel, if the image is coloured, then we have 3 coloured channels - which are Red, Green, Blue.<br>
- Does the CNN only accept the fixed input shapes?<br>
ans: Yes, it accepts only fixed input sizes. why? - The convolutional and pooling layers depend on fixed spatial dimensions to calculate feature maps and propagate through the network.<br>
- What is pooling?<br>
Ans: Downsampling the feature map(reduces the dimensions of the image). By feature map, we mean the output obtained by multiplying the image pixels by filter(matrix of weights)(this is also known as convolution). For demo, check this out https://deeplizard.com/resource/pavq7noze2 <br>
- What is max pooling?<br>
Ans: From the feature map, considering the window size and stride size. As, we move through the windows, we pick the maximum number in each window.(reduces the dimension of image by capturing the high level details.) <br>
- Why should we use pooling?<br>
Ans: The advantages of pooling are reduced computational cost(since the dimensions of the image are reduced) and translation invariance(Identifying features become location independent - meaning the model can capture the eyes of cat independent of its location(placement) in the image. <br>
- Why should we flatten out the tensors and use dense layers?<br>
Ans: At the end of the  CNN model we get the output in a 2D or 3D format, but our output is a scalar(1D). So, to get the desired output we flatten out the output add dense layers and the output layer along with respective activation function. <br>
- Why should we use softmax for multiclass classification and cross entropy loss?<br>
- What is data augmentation? <br>
Ans: Creating mutilple images from already exisiting image by performing some operations like shifting, rotating, transforming etc. Why is this useful? - Because in real world getting labelled data is very expensive, so even if we have less data we can use this technique to increase our data size. <br>


### Challenges I faced when working with Git in this project:

When pushing changes to a GitHub repository, you might encounter an error if files in your repository exceed GitHub's size limit (100MB). Even after deleting these files, the push might still fail because Git tracks changes, and the large files remain in the commit history. Below is a step-by-step guide to resolve this issue:

### Steps to Remove Large Files from Git History

1. **Check File Status:**
   - Use `git status` to confirm that the large files have been deleted from your working directory and staging area.

2. **Unstage and Remove Large Files:**
   - If any changes are still staged, unstage them using:
     ```bash
     git reset HEAD data/
     ```
   - Then, delete the files from your working directory:
     ```bash
     rm -rf data/
     ```

3. **Completely Remove Files from Git History:**
   - Use the `git-filter-repo` tool to remove the large files from your repository's commit history:
     1. Install the tool:
        ```bash
        pip install git-filter-repo
        ```
     2. Run the following command to delete the files from the commit history:
        ```bash
        git filter-repo --path <path_to_large_file> --invert-paths --force
        ```
        Replace `<path_to_large_file>` with the file paths of the large files (e.g., `fashion-mnist_train.csv`, `fashion-mnist_test.csv`).

4. **Reconfigure the Remote Repository:**
   - Add your GitHub repository as the remote origin (if needed):
     ```bash
     git remote add origin https://github.com/USERNAME/REPOSITORY_NAME.git
     ```
   - Verify the remote is correctly added:
     ```bash
     git remote -v
     ```

5. **Force Push the Cleaned History:**
   - Push the changes to the repository, forcing an update to overwrite the previous history:
     ```bash
     git push origin main --force
     ```

Following these steps ensures that the large files are entirely removed from your Git history, allowing your push to succeed without violating GitHub's size limits.

