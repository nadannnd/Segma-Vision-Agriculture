Coordinator Agent
===================

The **Coordinator Agent** acts as the central controller that orchestrates the execution of various task-specific agents based on the tasks decided by the **Input Agent**. This agent coordinates which task needs to be executed, depending on the user's query. It processes the response from the Input Agent, delegates tasks to the relevant agents, and gathers the results for further use.

Key Functions
------------------

1. **Task Decision:** The Coordinator uses the response from the **Input Agent** to decide which task(s) to run based on the user's query. The tasks could involve plant disease detection, crop yield prediction, weed detection, soil analysis, etc.

2. **Task Execution:** Once the relevant tasks are identified, the Coordinator Agent delegates the execution of these tasks to the appropriate agents, such as the **Plant Disease Agent**, **Crop Yield Agent**, etc. Each task may require either an image or non-image data to process.

3. **Aggregating Results:** After executing the tasks, the Coordinator collects and aggregates the results from the task-specific agents and returns them in a structured format.

Code Implementation
------------------

The code snippet below demonstrates the implementation of the **Coordinator Agent** in Python:

.. code-block:: python

    import json
    from input_agent import decide_tasks
    from plant_disease_agent import plant_disease_detection
    from crop_yield_agent import predict_crop_yield
    from weed_detection_agent import detect_weeds
    from soil_classification_agent import classify_soil

    def coordinate(user_input, image_path=None, non_image_data=None):
        """
        Orchestrates task-specific agents based on decisions from the Input Agent.
        """
        # Step 1: Use the Input Agent to decide tasks
        tasks_response = decide_tasks(user_input)
        tasks = json.loads(tasks_response)
        print(f"Tasks to run: {tasks}")

        # Step 2: Call task-specific agent functions
        results = {}

        for task in tasks:
            task_name = task["task"]
            image_required = task["image_required"]

            # Call the respective agent based on task name
            if task_name == "Plant disease detection" and image_required:
                results["Plant Disease Detection"] = plant_disease_detection(image_path)
            
            elif task_name == "Agriculture crop yield prediction" and not image_required:
                results["Crop Yield Prediction"] = predict_crop_yield(non_image_data)
            
            elif task_name == "Weed detection" and image_required:
                results["Weed Detection"] = detect_weeds(image_path)
            
            elif task_name == "Soil classification" and (image_required or non_image_data):
                results["Soil Classification"] = classify_soil(image_path or non_image_data)

        # Step 3: Return aggregated results
        return results


Next Steps:
------------------

To make the **Coordinator Agent** fully functional, you'll need to:

1. **Implement the Task-Specific Agents**: Implement functions for tasks like **plant disease detection**, **crop yield prediction**, etc.
2. **Handle Input Data**: Ensure that the required data (images or non-image data) is passed correctly to the task-specific agents.
3. **Extend for More Tasks**: As the project evolves, you can extend the **Coordinator Agent** to handle additional tasks such as weed detection, soil analysis, and plant identification by integrating the appropriate models and logic.

This setup provides a flexible and modular framework for orchestrating multiple task-specific agents, allowing you to scale and improve the system as needed.
