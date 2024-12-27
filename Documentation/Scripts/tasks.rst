Task-Specific Agents
========================

The **Task-Specific Agents** are responsible for performing specialized tasks identified by the **Input Agent** and orchestrated by the **Coordinator Agent**. Each task, such as **plant disease detection**, **crop yield prediction**, **weed detection**, etc., has its own dedicated agent that handles the task's specific requirements and processes the data (images or non-image data).

Overview of Task-Specific Agents
====================

Each task-specific agent performs a unique role based on the user’s query. The agents perform actions such as:

1. **Plant Disease Detection Agent**: Handles image analysis to detect and classify plant diseases.
2. **Crop Yield Prediction Agent**: Analyzes non-image data to predict agricultural crop yields based on historical and environmental data.
3. **Weed Detection Agent**: Detects weeds in agricultural images, distinguishing them from the crops.
4. **Soil Classification Agent**: Analyzes soil images or data to classify soil types for agricultural use.

Architecture
====================

The architecture of the multi-agent system is designed to be modular, with each agent handling a specific task. The **Coordinator Agent** calls upon each of these task-specific agents as needed, passing the appropriate data for processing.

Below is a high-level overview of how these agents interact:

.. image:: Documentation/Images/specif.png
   :alt: Task-Specific Agents Architecture  
   :width: 600px  
   :align: center  

---

## Detailed Presentation of Task-Specific Agents

### 1. **Plant Disease Detection Agent**
   - **Functionality**: This agent processes images of plants to detect potential diseases and classify them. It uses deep learning models trained on datasets of healthy and diseased plants.
   - **Input**: An image of the plant.
   - **Output**: A classification of whether the plant is healthy or diseased, and if diseased, the specific type of disease.

   **Use Case**: This agent helps farmers by identifying plant diseases early, allowing for prompt treatment.

### 2. **Crop Yield Prediction Agent**
   - **Functionality**: This agent predicts the crop yield based on non-image data such as historical crop data, environmental conditions, and geographical information.
   - **Input**: Non-image data (e.g., temperature, soil moisture, crop history).
   - **Output**: Predicted crop yield value.

   **Use Case**: This agent helps farmers estimate how much yield they can expect from a particular crop, assisting in planning and resource management.

### 3. **Weed Detection Agent**
   - **Functionality**: This agent analyzes images of agricultural fields to detect and segment weeds from crops. It uses deep learning models to identify weeds in various stages of growth.
   - **Input**: An image of an agricultural field.
   - **Output**: A classification of whether weeds are present in the image and their locations.

   **Use Case**: Weed management is a major concern for farmers, and this agent helps automate the process of weed detection, reducing labor costs and improving crop health.

### 4. **Soil Classification Agent**
   - **Functionality**: This agent analyzes soil data (either images or sensor data) to classify the soil type. Soil properties, such as pH, moisture content, and temperature, are used to determine soil suitability for different crops.
   - **Input**: Soil data or images.
   - **Output**: A classification of the soil type (e.g., Loam, Clay, Sandy, etc.).

   **Use Case**: This agent assists farmers in determining which crops will perform best in a given soil environment, optimizing agricultural practices.

---

### Integration in the System

Each of these task-specific agents is integrated within the multi-agent system. The **Coordinator Agent** determines which specific agent should be invoked based on the task at hand and manages the flow of data between them. This modular architecture allows for flexibility, where new agents can be added in the future to handle additional tasks in the agricultural domain.

---

This structure and the specialized functionality of each agent ensure that the **Segma-Vision Agriculture** project can address a variety of tasks with precision, enabling smarter and more efficient agricultural practices.
