# CommRank-HFG: LLM-Based Community Surveys for Operational Decision Making in Interconnected Utility Infrastructures

This repository contains the code, data, and experimental notebooks for our study on using Large Language Models (LLMs) to simulate community preferences for infrastructure repair prioritization. Our work demonstrates how synthetic persona preferences can complement technical repair prioritization models, providing a scalable proof of concept. Future work will focus on validating this approach with real community survey data and exploring transferability across communities using prior survey inputs.

## Repository Structure

### Jupyter Notebooks for Response Generation 
This shows the Jupyter notebooks used to generate persona responses under different prompt treatments. These notebooks use the synthetic persona datasets to run the LLM prompts and collect responses.

The notebooks correspond to the **community-unaware dataset (synthetic_personas_unbiased.json)**:
- `Unbiased_dataset_Original.ipynb`
- `Unbiased_dataset_InstructionFormat.ipynb`
- `Unbiased_dataset_RemoveSVS.ipynb`
- `Unbiased_dataset_Rewording_Question.ipynb`
- `Unbiased_dataset_Rewording_Reasoning.ipynb`
- `Unbiased_dataset_ShiftingTone.ipynb`
- `Unbiased_dataset_Choice_First.ipynb`

Each notebook collects persona responses for a specific prompt variation and prepares the data for further analysis.


### Synthetic Persona Datasets (`data/`)
This folder contains the synthetic persona datasets used for the experiments.

- `synthetic_personas_biased.json`: Synthetic personas generated with explicit community identity (referred to as the **community-aware dataset**).
- `synthetic_personas_unbiased.json`: Synthetic personas generated without assigned community identity (referred to as the **community-unaware dataset**).

These personas serve as the simulated participants for the infrastructure repair prioritization tasks. The datasets are used across all prompt variations to test how community awareness influences decision-making.


### Choice Data CSVs (`data/`)
This folder contains the aggregated persona choice data extracted from the raw LLM responses. Each CSV captures the pairwise infrastructure repair preferences collected under a specific prompt treatment:

- `personas_and_responses_biased.csv`
- `personas_and_responses_choice_first.csv`
- `personas_and_responses_instruction_format.csv`
- `personas_and_responses_shifting_tone.csv`
- `personas_and_responses_unbiased_original.csv`
- `personas_and_responses_unbiased_rewording_question.csv`
- `personas_and_responses_unbiased_rewording_reasoning.csv`
- `personas_and_responses_without_svs.csv`

Each file includes the pairwise comparisons used for training the comparator model.



### ComparatorChainization_Process.ipynb
Notebook for:
- Training the neural pairwise comparator.
- Applying the chainization method to generate global repair prioritization from the collected persona preferences.

### Additional Prompt Details
Detailed prompt templates and variations used in these experiments are provided in the file `Extra_Data_Information.pdf`. This file includes the exact wording, tone, and structure used.


## How to Use

1. Clone the repository:
```bash
git clone https://github.com/adaezy/CommRank-HFG.git
cd CommRank-HFG
```

2. Run the notebooks:
   
Execute the notebooks to generate persona responses and prepare the choice data.

4. Process the data:
   
Run the ComparatorChainization_Process.ipynb notebook to train the comparator model and generate the repair prioritization.


## License

This project is licensed under the MIT License.
