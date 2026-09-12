# Project DAMP: <img src="data/damp_logo.jpeg" height="100">
### Disagreements amongst AMP Model Predictions

> **Goal:** Understand the nature of disagreements between state-of-the-art antimicrobial peptide (AMP) classification and minimum inhibitory concentration (MIC) regression models.

In this table, I have collected candidate models with public prediction code and pretrained weights or documented weight downloads. 
It includes recent models and established baselines.

**Tasks:** `C` = AMP or antibacterial classification · `R` = continuous MIC regression · `P` = potency classification, such as low-MIC probability.

| Model | Task | Prediction output / biological target | Inference workflow | Weights and setup considerations |
|:------|:----:|:--------------------------------------|:-------------------|:--------------------------------|
| **[APEX](https://gitlab.com/machine-biology-group-public/apex)** | `R` | Species-specific MIC predictions across a bacterial panel | Peptides in `test_seqs.txt` → `predict.py` → `Predicted_MICs.csv`; [FASTA adapter](https://github.com/szczurek-lab/BattleAMP-apex) available | Pretrained ensemble; checkpoints included in the GitHub adapter |
| **[APEX Pathogen](https://gitlab.com/machine-biology-group-public/apex-pathogen)** | `R` | Species-specific MIC predictions against pathogens | Peptide-input prediction workflow documented in the repository README | Eight-model APEX ensemble documented; local execution and checkpoint retrieval remain unverified |
| **[AMPredictor](https://github.com/ruihan-dong/AMPredictor)** | `R` | Numerical log-MIC prediction using **graph neural networks + ESM-1b** | `preprocess.py` → `predict.py` | Trained `.model` included; ESM-1b feature generation required |
| **[MBC-Attention](https://github.com/jieluyan/MBC-Attention)** | `R` | *Escherichia coli* MIC regression | FASTA prediction function in `test_mbc_attention.py` | TensorFlow SavedModel included |
| **[ANIA](https://github.com/SilverGojo4/ANIA)** | `R` | Log-MIC for *E. coli*, *Pseudomonas aeruginosa* and *Staphylococcus aureus* | `src/main.py --stage infer_ania` | Three organism-specific `.pt` checkpoints included; sequence-encoding dependencies required |
| **[EvoGradient predictors](https://github.com/MicroResearchLab/AMP-potency-prediction-EvoGradient)** | `C` + `R` | AMP classification and MIC regression | `AMP_classification.py` and `AMP_regression.py` | `.pth` weights included; supplied scripts require a GPU |
| **[Deep_AMP](https://github.com/amirpandi/Deep_AMP)** | `R` | Gram-positive and Gram-negative MIC regression | Repository examples; [FASTA inference adapter](https://github.com/szczurek-lab/BattleAMP-deep-amp) available | Four CNN/LSTM SavedModels included |
| **[SenseXAMP](https://github.com/William-Zhanng/SenseXAMP)** | `C` + `R` | AMP classification; MIC regression for *E. coli* and *S. aureus* | ESM preprocessing and prediction scripts; [FASTA adapter](https://github.com/szczurek-lab/BattleAMP-senseXAMP) available | External checkpoint downloads required; downloads untested |
| **[AMPActiPred](https://github.com/lantianyao/AMPActiPred)** | `C` + `R` | Antibacterial classification, bacterial-target classification and MIC regression across ten species | FASTA → `predict.py` → JSON | External model downloads and model-path edits required; downloads untested |
| **[BERT MIC: EC/SA](https://github.com/janecai0714/AMP_regression_EC_SA)** | `R` | *E. coli* and *S. aureus* pMIC regression, exported as MIC in µM | `predict/predict.py`; Colab workflow available | External SharePoint checkpoints required; downloads untested |
| **[Macrel](https://github.com/BigDataBiology/macrel)** | `C` | AMP probability and class; additional hemolysis predictions | `macrel peptides --fasta …` | Pretrained ONNX models bundled |
| **[ampir](https://github.com/Legana/ampir)** | `C` | AMP probability using mature-peptide or precursor models | R function `predict_amps()` | Models bundled; choose the appropriate model for mature peptides versus precursors |
| **[AMPlify](https://github.com/BirolLab/AMPlify)** | `C` | AMP probability and class | `AMPlify -s input.fasta` | Balanced and imbalanced ensemble weights included; legacy TensorFlow environment |
| **[AMP Scanner v2](https://github.com/dan-veltri/amp-scanner-v2)** | `C` | AMP probability and class | `amp_scanner_v2_predict_tf1.py` | Three pretrained `.h5` models and environment files included; legacy TensorFlow |
| **[AI4AMP](https://github.com/LinTzuTang/AI4AMP_predictor)** | `C` | AMP probability and class | `PC6/PC6_predictor.py` | Trained `.h5` checkpoint included |
| **[amPEPpy](https://github.com/tlawrence3/amPEPpy)** | `C` | Random-forest AMP classification | `ampep predict` | Pretrained `amPEP.model` included |
| **[AMPidentifier](https://github.com/madsondeluna/AMPIdentifier)** | `C` | AMP probability and class from individual models or a voting ensemble | CLI or Python package | Trained models and feature scalers included |
| **[sAMPpred-GAT](https://github.com/HongWuL/sAMPpred-GAT)** | `C` | AMP classification using **graph attention networks** | Feature generation → `test.py` | Checkpoint included; requires trRosetta and sequence-alignment databases |
| **[HydrAMP classifiers](https://github.com/szczurek-lab/hydramp)** | `C` + `P` | AMP probability and low-MIC probability; no continuous MIC output | Separate FASTA adapters for [AMP classification](https://github.com/szczurek-lab/BattleAMP-hydramp-amp-classifier) and [MIC classification](https://github.com/szczurek-lab/BattleAMP-hydramp-mic-classifier) | Adapter weights included; peptides limited to 25 residues |
