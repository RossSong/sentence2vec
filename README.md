#  Deep sentence embedding using Sequence to Sequence learning

![screenshot](images/2d_pca_projection.png)

## Installing

1. [Install Torch](http://torch.ch/docs/getting-started.html).
2. Install the following additional Lua libs:

   ```sh
   luarocks install nn
   luarocks install rnn
   luarocks install penlight
   ```
   
   To train with CUDA install the latest CUDA drivers, toolkit and run:

   ```sh
   luarocks install cutorch
   luarocks install cunn
   ```
   
   To train with opencl install the lastest Opencl torch lib:

   ```sh
   luarocks install cltorch
   luarocks install clnn
   ```

3. Download the [Cornell Movie-Dialogs Corpus](http://www.mpi-sws.org/~cristian/Cornell_Movie-Dialogs_Corpus.html) and extract all the files into data/cornell_movie_dialogs.

## Training

```sh
th train.lua [-h / options]
```

Use the `--dataset NUMBER` option to control the size of the dataset. Training on the full dataset takes about 5h for a single epoch.

The model will be saved to `data/model.t7` after each epoch if it has improved (error decreased).

## Getting a pretrained model
Download:

1. The pretraned [model.t7](https://drive.google.com/file/d/0BwsDa5L6bdMpTC1GUEtPbWE2Zms/view?usp=sharing)
2. Vocabulary [vocab.t7](https://drive.google.com/file/d/0BwsDa5L6bdMpQV9zOTRhZlNPWG8/view?usp=sharing)

Put them into the `data` directory.

## Extracting embeddings from sentences
Run the following command
```sh
th -i extract_embeddings.lua --model_file data/model.t7 --input_file data/test_sentences.txt --output_file data/embeddings.t7 --cuda
```

To visualize 2D projections of the embeddings refer to: [example.ipynb](https://github.com/kostyaev/sentence2vec/blob/master/example.ipynb)

## Acknowledgments
This implementation utilizes code from [Marc-André Cournoyer's repo](https://github.com/macournoyer/neuralconvo)

## License
MIT License
