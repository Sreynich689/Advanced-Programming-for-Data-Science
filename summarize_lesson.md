# Class Activity Summary – ADV

## Lesson Summary: Hugging Face, Unsloth, and LLM Fine-Tuning

## 1. Hugging Face

### 1.1 What is Hugging Face?

Hugging Face is an open-source AI platform and community where developers and researchers can find, share, and use pre-trained AI models, datasets, and machine learning tools.

It provides resources for Natural Language Processing (NLP), Large Language Models (LLMs), computer vision, audio processing, and other AI tasks.

### 1.2 Main Purposes of Hugging Face

- **Models:** Provides access to pre-trained AI models such as Llama, Qwen, and Mistral.
- **Datasets:** Provides datasets for training, validation, and testing AI models.
- **Spaces:** Allows users to explore and share AI applications and demonstrations.
- **Libraries:** Provides tools such as Transformers and Datasets for machine learning development.

### 1.3 What is Fine-Tuning?

Fine-tuning is the process of taking an existing pre-trained model and training it further with a specific dataset to improve its performance on a particular task.

Instead of training a model from scratch, fine-tuning uses the knowledge already learned by the model and adapts it to a specific purpose.

**Example:** A general-purpose language model can be fine-tuned with customer service data to become better at answering customer questions.

### 1.4 Understanding Hugging Face Datasets

A dataset is a collection of information used to train or evaluate an AI model.

Hugging Face provides a large collection of datasets that users can explore and use for machine learning tasks.

Important concepts:

- **Dataset Viewer:** Allows users to inspect dataset contents directly on the website.
- **Features or Columns:** Describe the different fields contained in a dataset.
- **Rows:** Represent individual examples in the dataset.
- **Training Split:** Contains data used to train the model.
- **Validation Split:** Contains data used to monitor and evaluate model performance during training.
- **Testing Split:** Contains data used for final model evaluation.

### 1.5 Dataset Preparation

Dataset preparation is an important step before fine-tuning.

It involves inspecting, cleaning, organizing, and formatting data into a structure that the model can understand.

Important preparation steps include:

- Checking the dataset structure.
- Identifying missing or incorrect information.
- Removing unnecessary or duplicate data.
- Formatting the data into the appropriate structure.
- Ensuring the dataset is suitable for the target task.

---

## 2. Unsloth

### 2.1 What is Unsloth?

Unsloth is an open-source library designed to make fine-tuning Large Language Models (LLMs) faster and more memory-efficient.

It provides optimized training techniques that help developers fine-tune large models using fewer GPU resources and less training time in supported configurations.

### 2.2 Main Purposes of Unsloth

- Reduce GPU memory consumption.
- Improve training speed.
- Support efficient fine-tuning techniques such as LoRA and QLoRA.
- Make fine-tuning large language models more accessible.
- Support popular language models such as Llama and Qwen.

### 2.3 Why Use Unsloth?

Fine-tuning large language models normally requires significant computational resources.

Unsloth helps reduce these requirements through optimization techniques, making it easier to fine-tune models even when hardware resources are limited.

---

## 3. Model Selection

### 3.1 What is Model Selection?

Model selection is the process of choosing the most suitable pre-trained model for a specific task.

Different models have different architectures, capabilities, sizes, and computational requirements. Therefore, selecting the right model is important for achieving good performance.

### 3.2 Important Factors in Model Selection

**1. Task Alignment**

The selected model should match the purpose of the project.

For example:

- Text generation requires a language generation model.
- Text classification requires a model suitable for classification.
- Image recognition requires a vision model.
- Speech recognition requires an audio model.

**2. Model Architecture**

Model architecture describes how the model is designed and how it processes information.

Common architectures include:

- **Encoder-only:** Commonly used for understanding and analyzing text. Example: BERT.
- **Decoder-only:** Commonly used for generating text. Examples: Llama and Qwen.
- **Encoder-decoder:** Commonly used for transforming one sequence into another. Example: T5.

**3. Model Size and Complexity**

Model size refers to the number of parameters in a model.

Larger models generally require more memory and computational resources. Smaller models are usually easier to run but may have different performance capabilities.

**4. Performance Benchmarking**

Performance benchmarking is the process of comparing models using evaluation metrics and standardized tests.

Common evaluation metrics include accuracy, precision, recall, F1-score, and perplexity, depending on the task.

**5. Community Support and Documentation**

Models with good documentation and active communities are easier to understand, implement, and troubleshoot.

---

## 4. Model Loader

### 4.1 What is a Model Loader?

A model loader is responsible for loading a pre-trained model and its learned weights into memory so that it can be used for training, fine-tuning, or making predictions.

The model contains parameters (weights) that represent the knowledge it has learned during the pre-training process.

### 4.2 Common Types of Model Loaders

**1. AutoModel**

AutoModel automatically identifies and selects the appropriate model architecture based on the model configuration.

Its main advantage is flexibility because it can work with different supported model architectures without manually specifying the exact model class.

**2. Specific Model Class**

A specific model class loads a model using its exact architecture.

It is useful when the developer already knows which model architecture is required.

### 4.3 Difference Between AutoModel and Specific Model Class

- **AutoModel:** Automatically selects the appropriate model architecture.
- **Specific Model Class:** Directly specifies the architecture that should be loaded.

Both methods are used to load pre-trained models, but they differ in how the model architecture is selected.

---

## 5. Processor Loader

### 5.1 What is a Processor?

A processor prepares raw input data before sending it to a model.

Depending on the model, it can handle text, images, audio, or multiple types of input.

Its purpose is to convert raw information into a format that the model can understand.

### 5.2 AutoProcessor

AutoProcessor automatically selects the appropriate processor based on the model configuration.

It can handle different types of preprocessing, including:

- Text tokenization.
- Image resizing and normalization.
- Audio preprocessing.
- Preparing multimodal inputs.

### 5.3 Difference Between Tokenizer and Processor

**Tokenizer:**

A tokenizer mainly handles text. It converts words and sentences into smaller units called tokens and then converts those tokens into numerical IDs that a language model can process.

**Processor:**

A processor can handle multiple types of data, including text, images, and audio, depending on the model.

Therefore, a tokenizer is mainly designed for text processing, while a processor provides broader input-processing capabilities.

---

## 6. LoRA (Low-Rank Adaptation)

### 6.1 What is LoRA?

LoRA stands for Low-Rank Adaptation. It is a Parameter-Efficient Fine-Tuning (PEFT) technique that allows developers to adapt pre-trained models without updating all of their original weights.

Instead of training the entire model, LoRA freezes the original model weights and introduces two smaller trainable matrices, called A and B.

These matrices learn the necessary changes to adapt the model to a specific task.

### 6.2 How LoRA Works

In traditional full fine-tuning:

- All or most of the model's original parameters are updated.
- It requires more GPU memory.
- It can require more computational resources.

With LoRA:

- The original model weights remain frozen.
- Only the additional LoRA parameters are trained.
- The number of trainable parameters is reduced.
- Fine-tuning becomes more memory-efficient.

### 6.3 Understanding LoRA Matrices

LoRA introduces two smaller matrices:

- **Matrix A:** Reduces the original weight representation into a lower-dimensional space.
- **Matrix B:** Projects the lower-dimensional representation back to the original output dimension.

Together, these matrices learn a weight update that is added to the original model weights.

The main idea is that the model does not need to update every original parameter to learn a new task.

### 6.4 Example of Parameter Reduction

Suppose an original weight matrix contains:

- Full fine-tuning: 262,144 parameters.
- LoRA with rank 8: 8,192 trainable parameters.

This means LoRA reduces the number of trainable parameters by approximately 97% in this example.

This reduction helps decrease memory requirements and makes fine-tuning more efficient.

**Note:** The actual parameter reduction depends on the model architecture, LoRA rank, and selected layers.

---

## 7. Full Fine-Tuning vs LoRA vs QLoRA

These are three important approaches to fine-tuning language models.

### 7.1 Full Fine-Tuning

Full fine-tuning updates all or most of the original model parameters using a new dataset.

**Advantages:**

- Allows the entire model to adapt to the new task.
- Provides flexibility in modifying model behavior.

**Disadvantages:**

- Requires more GPU memory.
- Requires more computational resources.
- Can take longer to train.

### 7.2 LoRA

LoRA freezes the original model weights and trains additional low-rank matrices.

**Advantages:**

- Reduces the number of trainable parameters.
- Requires less memory than full fine-tuning.
- Makes model adaptation more efficient.

### 7.3 QLoRA

QLoRA stands for Quantized Low-Rank Adaptation.

It combines quantization with LoRA. The original model is loaded in a lower-precision format, commonly 4-bit, while the LoRA adapters are trained.

**Advantages:**

- Further reduces memory requirements.
- Allows fine-tuning larger models with limited GPU resources.
- Combines the efficiency of quantization and LoRA.

### 7.4 Comparison

| Method | Main Concept | Main Advantage |
|---|---|---|
| Full Fine-Tuning | Updates original model weights | Entire model can adapt |
| LoRA | Trains additional low-rank matrices | Fewer trainable parameters |
| QLoRA | Combines quantization and LoRA | Lower memory requirements |

---

## 8. Complete Fine-Tuning Workflow

Fine-tuning involves several connected steps. Each step plays an important role in preparing and adapting a pre-trained model.

### 8.1 Workflow

1. **Model Selection:** Choose a suitable pre-trained model based on the task.
2. **Model Loading:** Load the model and its pre-trained weights into memory.
3. **Processor or Tokenizer Loading:** Prepare the input data so the model can understand it.
4. **Dataset Loading:** Find and load a suitable dataset from Hugging Face or another source.
5. **Dataset Preparation:** Inspect, clean, and format the dataset.
6. **Fine-Tuning Method Selection:** Choose an appropriate method, such as full fine-tuning, LoRA, or QLoRA.
7. **Training Configuration:** Determine the training settings, including learning rate, batch size, and number of epochs.
8. **Model Training:** Train the model using the prepared dataset.
9. **Model Evaluation:** Test the fine-tuned model to measure its performance.
10. **Model Saving:** Save the trained model or its adapters for future use.

---

## 9. Key Concepts Learned

| Concept | Main Purpose |
|---|---|
| Hugging Face | Provides pre-trained models, datasets, and AI tools |
| Fine-Tuning | Adapts an existing model to a specific task |
| Unsloth | Makes LLM fine-tuning faster and more memory-efficient |
| Model Selection | Chooses the appropriate model for a task |
| Model Loader | Loads the pre-trained model and its weights |
| Processor Loader | Prepares input data for the model |
| Tokenizer | Converts text into numerical tokens |
| Dataset Preparation | Cleans and organizes data for training |
| LoRA | Reduces the number of trainable parameters |
| QLoRA | Combines quantization with LoRA to reduce memory usage |

---

## Conclusion

Throughout this lesson, I learned the fundamental concepts of Large Language Model fine-tuning and the tools used in the process.

First, I learned that Hugging Face provides a platform where developers can find pre-trained models and datasets. It also provides tools for exploring, loading, and preparing datasets for machine learning tasks.

Next, I learned about Unsloth and how it helps make fine-tuning more efficient by reducing training time and memory consumption.

I also learned the importance of model selection, model loaders, and processor loaders. Choosing the right model and preparing input data correctly are important steps before starting the training process.

Finally, I learned about LoRA and QLoRA, which are efficient fine-tuning techniques that reduce the number of trainable parameters and the memory required.

Overall, this lesson helped me understand that fine-tuning is not simply training a model. It involves selecting an appropriate model, preparing a suitable dataset, choosing an efficient training method, and evaluating the final result.

**Key Takeaway:** Fine-tuning allows us to adapt an existing pre-trained AI model to a specific task without always needing to train a completely new model from scratch.

---

*End of Class Activity Summary – ADV*