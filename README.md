🦙 Llama 3.2-1B Hinglish Fine-Tuning (LoRA)
Overview & Features
This repository contains a lightweight Proof of Concept (PoC) for fine-tuning the meta-llama/Llama-3.2-1B model on a custom Hindi/Hinglish dataset. It utilizes Parameter-Efficient Fine-Tuning (PEFT) to make the training process accessible without requiring massive computational resources.

PEFT / LoRA Integration: Targets the q_proj and v_proj modules to significantly reduce trainable parameters (only ~0.06% of the model is updated).

Supervised Fine-Tuning: Leverages Hugging Face's trl library and SFTTrainer for streamlined training.

Custom Instruction Formatting: Implements a clean ### Instruction: and ### Output: prompt template.

Quick Start
To run this pipeline locally, you will need to install the required dependencies and execute the training script.

1. Install Dependencies:

Bash
pip install torch transformers peft trl datasets
2. Prepare the Data:
The script currently generates a data.jsonl file with a small batch of 5 Hinglish Q&A examples. You can replace this list with your own extensive dataset.

3. Run the Training:
Execute the provided Jupyter Notebook or Python script. The fine-tuned weights and tokenizer will be saved to the ./fine-tuned-llama directory.

Limitations & Scaling Up
This repository is currently configured as a structural template. Out of the box, it is set to run on a CPU (use_cpu=True) with only 5 training examples.

To achieve coherent, high-quality text generation, you must update the following:

Hardware: Switch to a GPU setup by setting use_cpu=False in the SFTConfig.

Dataset Size: Increase the training data from 5 examples to at least 500–1,000 high-quality instructional pairs.

Hyperparameters: Adjust the batch size, learning rate, and epochs based on your hardware capabilities.
