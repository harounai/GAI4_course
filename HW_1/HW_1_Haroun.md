# GAI4 - Assignment 01

## <center><u>**EfficientNet-B0 on UC Merced Dataset**</u></center>

### **What we did**

We trained two versions of the same neural network (EfficientNet-B0) to classify aerial images into 21 land-use categories (forest, beach, runway, etc.). The dataset has 2,100 images split into **70% training / 15% validation / 15% test**, with exactly equal samples per class.

- **Model A** — trained from random weights (no prior knowledge)
- **Model B** — started from ImageNet weights (already knows what things look like)


### **Results**

| | From Scratch | Pretrained |
|---|---|---|
| Test Accuracy | 33.65% | **95.56%** |
| Balanced Accuracy | 33.65% | **95.56%** |


### **Training Curves**

![Scratch vs Pretrained Training Curves]("Scratch.png")

The difference is striking. The pretrained model shot up to ~90% accuracy within the first 3 epochs and stayed there. The scratch model slowly crawled from 5% to 33% over all 20 epochs, with a noisy and unstable validation curve.


### **Which classes were hardest?**

For the scratch model, the trickiest classes were the three residential types — **dense, medium, and sparse residential** — because they all look very similar from above (rooftops, roads, some greenery). The model often mixed them up.

The pretrained model had almost no trouble with any class, keeping F1-scores above 0.86 across the board.


### **Key Takeaway**

With only 70 images per class, training from scratch simply doesn't work well — there's not enough data for the model to learn what anything looks like. Starting from ImageNet weights gives the model a massive head start (it already understands textures, shapes, edges), so it only needs a few epochs to adapt to aerial imagery.

> **Pretrained = 95.56% accuracy in ~5 epochs. Scratch = 33.65% after 20 epochs.**
> Transfer learning wins by a landslide on small datasets.