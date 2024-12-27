.. Plant Disease Detection Agent
===============================

The **Plant Disease Detection Agent** is designed to analyze images of plants to identify and classify potential diseases. This task-specific agent plays a critical role in agricultural applications by enabling early detection of plant diseases, helping farmers take timely actions to prevent further spread and loss of crops.

### Overview of Plant Disease Detection
--------------------------------------

The agent uses advanced deep learning models to process images of plants, detect symptoms of diseases, and classify the diseases based on known plant disease datasets. It helps in identifying various plant diseases from the visual symptoms presented on the plant's leaves, stems, and other parts. 

### Functionality
-----------------
- **Input**: The agent receives images of plants, typically taken with a camera or mobile device. 
- **Processing**: It processes the images using a pre-trained or fine-tuned deep learning model such as a Convolutional Neural Network (CNN).
- **Output**: The agent classifies whether the plant is healthy or affected by a specific disease. In the case of disease detection, it also provides the type of disease affecting the plant.

### Use Case
-------------
Plant disease detection can significantly reduce crop loss by enabling farmers to detect diseases at an early stage. Timely intervention and treatment can prevent the spread of disease to other plants and optimize agricultural productivity.

### Architecture
-------------
The architecture of the **Plant Disease Detection Agent** follows a modular deep learning approach, where the fine-tuning process adapts a pre-trained model to recognize specific plant diseases. The process includes:
- Image preprocessing to ensure input images are in the required format.
- Fine-tuning a pre-trained model such as **GroundingDINO** on plant disease datasets like **PlantVillage** and **PlantDoc**.
- Using the fine-tuned model for prediction and classification.

Below is a high-level architecture diagram of the Plant Disease Detection system:

.. image:: Documentation\Images\crop.png  
   :alt: Plant Disease Detection Architecture  
   :width: 600px  
   :align: center  

### Fine-Tuning the Model
-------------------------
The fine-tuning process involves adapting a pre-trained deep learning model to the specific task of plant disease detection. The **GroundingDINO** model, initially pre-trained on general datasets, was fine-tuned using the **PlantVillage** and **PlantDoc** datasets. These datasets contain images of healthy and diseased plants across various species, making them ideal for training models to detect plant diseases.

### Colab Notebook for Fine-Tuning
---------------------------------
The fine-tuning of the model was conducted in a Google Colab notebook. The notebook demonstrates the step-by-step process of preparing the dataset, adjusting the model architecture, training the model, and saving the fine-tuned weights for later use.

You can access the notebook used for fine-tuning the **GroundingDINO** model on plant diseases here:

.. raw:: html
   <a href="https://colab.research.google.com/drive/1A5wfaaOKIVnll9-w3K_Q8bOLCWgp5M_7?usp=sharing" target="_blank">Plant Disease Fine-Tuning Notebook</a>

**Colab Notebook Link**: [Plant Disease Fine-Tuning Notebook](https://colab.research.google.com/drive/1A5wfaaOKIVnll9-w3K_Q8bOLCWgp5M_7?usp=sharing)

In this notebook, we:
1. Load and preprocess the **PlantVillage** and **PlantDoc** datasets.
2. Fine-tune the model using the datasets to detect diseases such as **Powdery Mildew**, **Rust**, and **Blight**.
3. Save the fine-tuned model weights for deployment in the **Plant Disease Detection Agent**.

### Integration with Segma-Vision
--------------------------------
The fine-tuned model is integrated into the **Segma-Vision Agriculture** project. The **Plant Disease Detection Agent** is invoked by the **Coordinator Agent** when the user's query specifies a need for plant disease identification. The agent processes the image, predicts the disease, and returns the results to the user.

Here’s an overview of how the **Plant Disease Detection Agent** is integrated into the **Segma-Vision** workflow:

1. The **Input Agent** determines the task based on user input (e.g., "Analyze this plant for diseases").
2. The **Coordinator Agent** routes the task to the appropriate agent (in this case, the **Plant Disease Detection Agent**).
3. The **Plant Disease Detection Agent** receives the image, runs the fine-tuned model, and classifies the plant’s condition.
4. The result is returned to the user with the classification of the plant's disease or a message indicating it is healthy.

### Code Overview
----------------
Here is the code for the **Plant Disease Detection Agent**:

.. code-block:: python

    from plant_disease_agent import plant_disease_detection

    def plant_disease_detection(image_path):
        """
        This function processes the image and predicts the plant's disease.
        """
        # Load the fine-tuned model
        model = load_finetuned_model()

        # Preprocess the image
        image = preprocess_image(image_path)

        # Predict the disease
        prediction = model.predict(image)

        # Return the predicted disease
        return prediction

    def load_finetuned_model():
        """
        Loads the fine-tuned GroundingDINO model for plant disease detection.
        """
        model_path = "path_to_finetuned_model"
        model = load_model(model_path)
        return model

    def preprocess_image(image_path):
        """
        Preprocesses the image for the model input (e.g., resizing, normalization).
        """
        image = load_image(image_path)
        image = resize_image(image, target_size=(224, 224))  # Example size
        image = normalize_image(image)
        return image

---

This agent integrates seamlessly into the **Segma-Vision Agriculture** multi-agent system, providing a crucial service for plant disease identification and helping optimize agricultural practices through early detection of plant diseases.

**See the Segma-Vision integration documentation for further details on the architecture and system flow.**

---

For more information, check out the [Segma-Vision Notebook](https://github.com/MasrourTawfik/SegmaVisionPro/blob/main/SegmaVisionPro_Test_NoteBook2.ipynb).
