# Linear SVM Visualizer

An interactive, dark-themed website that helps beginners understand how a Linear Support Vector Machine (SVM) works. Add data points, adjust hyperparameters, and watch the model learn step by step.

Built with HTML, CSS, and JavaScript in a single file, ready to deploy on GitHub Pages.

## About Linear SVM

A Linear SVM learns a straight decision boundary that separates two classes. It balances creating a wide margin with penalizing points that are misclassified or fall inside that margin.

This visualizer uses full-batch subgradient descent to update the model’s weights and bias.

## Features

- **Interactive data canvas:** Add points from two classes, delete individual points, or generate a random dataset.
- **Spray brush:** Click and drag to scatter points randomly inside an adjustable circular nozzle.
- **Brush eraser:** Delete points inside the nozzle area by clicking or dragging.
- **Nozzle preview:** See the brush area before adding or erasing points.
- **Adjustable hyperparameters:** Change the learning rate and regularization parameter C.
- **Step-by-step training:** Perform one training update at a time.
- **Automatic training:** Play until the stopping condition or epoch limit is reached, with the option to pause.
- **Decision boundary:** Observe the separating line and its margin boundaries.
- **Model state:** View the current epoch, weights, bias, and hyperplane equation.
- **Live calculation details:** Inspect previous and new weights, bias updates, inferred gradients, margin violations, and the objective change after each observed training step.
- **Independent scrolling:** Scroll the left and right columns separately on desktop.
- **Loss graph:** Track the SVM objective during training.
- **Reset controls:** Reset the model or clear all data points.
- **Responsive interface:** Use the website on desktop and smaller screens.

## Technologies

- HTML5
- CSS3
- JavaScript
- HTML Canvas API
- Google Fonts: Economica and Carter One
- GitHub Pages for hosting

No frameworks, build tools, or package installation are required.

## Run Locally

1. Clone the repository:

   ```bash
   git clone https://github.com/watchied/Support-Vector-Machine.git
   ```

2. Open the project folder:

   ```bash
   cd Support-Vector-Machine
   ```

3. Open the website HTML file in your browser. The examples below use `index-fixed.html`. 

   On macOS:

   ```bash
   open index-fixed.html
   ```

An internet connection is needed to load Google Fonts. The visualizer itself runs locally in the browser.

## How to Use

1. Click **Random Data** to generate a dataset, or click **Clear** to start with an empty canvas.
2. Select **Class 1 (Blue)** or **Class 2 (Orange)**.
3. Select **ADD** and choose **Single point** to add one point per click.
4. Choose **Spray**, select a class, and click or drag on the canvas to scatter points.
5. Adjust **Nozzle size** from 10 to 100 pixels. This is the brush diameter on screen.
6. Select **DELETE** and click or drag to erase points within the nozzle. Right-clicking uses the original nearest-point deletion behavior.
7. Adjust **C (regularization)** and **Learning rate** within their displayed ranges.
8. Click **STEP** for one training update, or **Play until Convergence** to train automatically. Click **Pause** to stop automatic training.
9. Observe the boundary, model parameters, **Current update** calculations, and loss graph.
10. Click **Reset** to reset the model while keeping the dataset, or **Clear** to remove all points.

Point creation is limited to 2,000 points to help keep the interface responsive. Spray mode places up to six points per stamp; points outside the canvas are skipped.

Training requires at least one point from each class. Changing the dataset or hyperparameters resets the model.

## Hyperparameters

| Parameter | Description |
|-----------|-------------|
| C | Controls the penalty for margin violations relative to weight regularization. |
| Learning rate | Controls the size of each weight and bias update. |
| Max epochs | Fixed at 3,000 in the current implementation. |

## Brush Controls

| Control | Behavior |
|---------|----------|
| Single point | Adds one point with the selected class per click. |
| Spray | Adds random points inside the nozzle while clicking or dragging. |
| Nozzle size | Sets the spray and eraser diameter from 10 to 100 screen pixels. |
| DELETE | Removes all points within the brush area. |
| Right-click | Removes the nearest point within the original deletion threshold. |

## Training Objective

The model minimizes an L2 regularization term plus the average hinge loss:

**Objective = ½ ‖w‖² + C × mean(max(0, 1 − yᵢ(w · xᵢ + b)))**

Where:

- **w** is the weight vector.
- **b** is the bias.
- **xᵢ** is a data point.
- **yᵢ** is its class label: +1 or −1.
- **C** controls the penalty for margin violations.

Automatic training stops when the objective changes by less than 0.00005 for 20 consecutive updates, or when it reaches 3,000 epochs. This is a practical stopping rule rather than a guarantee of the exact optimum.

## Interface Layout

| Area | Purpose |
|------|---------|
| Top-left | Data canvas and point controls |
| Bottom-left | Hyperparameters and training controls |
| Top-right | Model state and explanations |
| Bottom-right | Loss graph and training feedback |
| Footer | Group members and CEi KMITL |

The desktop columns scroll independently. On small screens, panels stack vertically and the page scrolls normally.

## Project Structure

- `index.html` — Complete website, including HTML, CSS, and JavaScript.
- `README.md` — Project overview and usage instructions.

If your repository currently uses `index-fixed.html`, that file contains the application instead. For a GitHub Pages homepage, save the intended final version as `index.html` in the published folder.

## Group Members

| Name | Student ID |
|------|------------|
| Patchpakintr Chiwkha | 67011242 |
| Watcharathorn Krachangmon | 67011380 |
| Worawalun Sombutphotiudom | 67011385 |
| Kittisak Chalongkulwat | 67011613 |
| Sirawich Sromcheep | 67011655 |
| Techin Lohapongpan | 67011660 |

**Computer Engineering (International) — KMITL**

## Limitations

- Supports two classes and two input features.
- Uses a linear decision boundary, so it cannot fully separate every dataset.
- The objective may fluctuate during training because the learning rate is fixed.
- Designed for educational visualization rather than production machine learning.
