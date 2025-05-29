# DL_fashion

## Local project Set up:

We are using a subset of the Deep Fashion Dataset for Fashion Syntehsis. This is a link to the dataset description: https://mmlab.ie.cuhk.edu.hk/projects/DeepFashion/FashionSynthesis.html. 

There are about 80k images with descriptions provided. We emailed for dataset access and have the passwords. Process to accessing dataset in drive is below, follow it exactly. We are working in Google Colab. 

1. Access the google drive image data at: https://mmlab.ie.cuhk.edu.hk/projects/DeepFashion/FashionSynthesis.html (Once on this link click "Google Drive" on the first page and it will direct you to your drive with the shared data)

2. Add a shortcut of the Fashion Syntehsis from your shared drive to your google drive.

3. Update the pathway of the Google Colab file to where the shortcut exists in your drive.

4. Run the Google Colab and make sure everything is accessed ok and works. If you run into any access issues here is the password for accessing the encrypted image ZIP files:
  mmlab_DeepFashion_fashionsynth

## Data Processing: 

Review google colab notebook in GIT. It has all of the distribution data regarding each image and its description. Gender and Sleeve mapping have specific information in each descrption and have been label encoded. We have also label encoded general fashion descriptory terms which can be reviewed in the code. Additional labels are not comprehensive but our best guess as to what descriptions will include. 

Note: Since this data is protected you can not view the files directly through drive and they are too large to download, so everything must be done via google colab where we have set up an environment to access the protected files locally in google drive. 

We have included a range of graphs and visualizations for the data regarding what images we are working with. Please review those graphs. 

## Fine-Tuning CLIP
Review the `clip_finetuning.ipynb` file in the repository. This notebook contains the DataLoader class as well. To fine-tune the model you can run the cell containing the training loop. Make sure all the paths in each of the cells are updated according to your project directory on your Google Collab instance. Additionally, the last two cells in the notebook serve as an evaluation to compare the pretrained CLIP encoder and the finetuned CLIP encoder. The number of samples the model is evaluated on is currently set at 5,000 but can be changed to any number less than the size of the dataset.

## Fine-Tuning Model & Generating Images
Review the `my_deep_fashion_fine_tuning.ipynb` file in the repository. This notebook contains the DataLoader class, which is used to load data from the Fashion Synthesis Benchmark dataset for training. Make sure the notebook is placed in the same directory as the Fashion Synthesis Benchmark folder and the `G2.h5` file. The dataset resides inside the Fashion Synthesis Benchmark folder.

To fine-tune the model, open the notebook and run the cells. Make sure to change the paths based on where your directory sits in Drive. You can customize the training by adjusting parameters such as the number of images, the number of epochs, and the learning rate. When calling the train() function, pass the desired values for these hyperparameters. Based on our experiments, the model that gave the lowest loss had the following hyperparameter values: 20 images, 5 epochs, and a learning rate of 5e-5. After training is complete, the model will automatically be saved into the project_models directory.

To generate images, first select the trained model you would like to use and specify its path when initializing the `StableDiffusionPipeline`. There are sample prompts provided in the notebook, but you can try different clothing prompts by adding them to the prompt_list variable. After setting your prompts, continue running the remaining cells to generate images and compute the Inception Score, which helps evaluate the quality and diversity of the generated images.
