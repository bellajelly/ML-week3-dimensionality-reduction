# Week 3: Dimensionality Reduction Analysis

**Author:** Bell Jelly  
**Course:** Machine Learning  
**Institution:** [Your Institution]  
**Date:** February 2026

---

## Project Overview

This project explores dimensionality reduction techniques applied to a physical gene regulatory network from *Caenorhabditis elegans* (C. elegans). Rather than using standard datasets like Iris or MNIST, this analysis investigates biologically meaningful data to understand how PCA and t-SNE reveal different patterns in complex biological systems.

### Research Questions

1. How do transcription factors cluster based on their regulatory targets?
2. How do genes cluster based on their structural roles in the regulatory network?
3. What information is lost when we reduce high-dimensional biological data to 2D?
4. How can dimensionality reduction introduce bias in biological research?

---

## Dataset

**Source:** Physical Gene Regulatory Networks in C. elegans  
**Files:**
- `TableS1_datasets_for_prior.csv`: Metadata about 168 experimental datasets
- `TableS3_WT_functional_priors.csv`: Gene regulatory network with 127,479 interactions

**Network Statistics:**
- 289 unique regulator genes (transcription factors)
- 19,185 unique target genes
- Directed network structure (regulator → target)

---

## Methods

### Option A: Regulatory Target Analysis
- **Data structure:** 289 regulators × 19,185 targets (binary matrix)
- **Approach:** Cluster transcription factors by which genes they regulate
- **Biological insight:** Reveals functional modules and co-regulated gene programs

### Option B: Network Topology Analysis
- **Data structure:** All genes × 5 network features
  - Out-degree (genes regulated by this gene)
  - In-degree (genes regulating this gene)
  - Betweenness centrality (bridging position)
  - Clustering coefficient (local connectivity)
  - PageRank (network importance)
- **Approach:** Cluster genes by their structural role in the network
- **Biological insight:** Reveals hub genes, bottlenecks, and network architecture

### Dimensionality Reduction Techniques

**Principal Component Analysis (PCA):**
- Linear method
- Preserves global variance structure
- Interpretable through component loadings
- Reports explained variance ratio

**t-Distributed Stochastic Neighbor Embedding (t-SNE):**
- Non-linear method
- Preserves local neighborhood structure
- Better at revealing distinct clusters
- Perplexity = 30, iterations = 1000

---

## Repository Structure

```
week3-dimensionality-reduction/
├── README.md                                    # This file
├── dimensionality_reduction_analysis.ipynb     # Main analysis notebook
├── ethical_reflection.md                       # Ethical considerations
└── data/
    ├── TableS1_datasets_for_prior.csv
    └── TableS3_WT_functional_priors.csv
```

---

## Running the Analysis

### Option 1: Google Colab (Recommended)

1. **Open the notebook in Colab:**
   - Go to [Google Colab](https://colab.research.google.com)
   - Click "File" → "Open notebook" → "GitHub"
   - Enter URL: `https://github.com/bellajelly/week3-dimensionality-reduction`
   - Select `dimensionality_reduction_analysis.ipynb`

2. **The notebook will automatically:**
   - Load data directly from this GitHub repository
   - Install required packages
   - Run all analyses
   - Generate visualizations

3. **No local setup required!**

### Option 2: Local Jupyter

**Prerequisites:**
- Python 3.8+
- Jupyter Notebook or JupyterLab

**Installation:**

```bash
# Clone the repository
git clone https://github.com/bellajelly/week3-dimensionality-reduction.git
cd week3-dimensionality-reduction

# Install required packages
pip install numpy pandas matplotlib seaborn scikit-learn networkx

# Launch Jupyter
jupyter notebook dimensionality_reduction_analysis.ipynb
```

**Required packages:**
- `numpy` - Numerical computing
- `pandas` - Data manipulation
- `matplotlib` - Visualization
- `seaborn` - Statistical visualization
- `scikit-learn` - PCA, t-SNE, StandardScaler
- `networkx` - Network analysis

---

## Key Results

*[To be completed after running the analysis]*

### Option A: Regulatory Targets
- PCA explained variance: XX%
- Distinct clusters observed: [Yes/No]
- Biological interpretation: [Summary]

### Option B: Network Topology
- PCA explained variance: XX%
- Hub genes identified: [List key genes]
- Network structure revealed: [Summary]

### Comparison
- Do the two approaches give similar or different clustering?
- Which genes appear important in one view but not the other?
- Example: lin-42 (clock gene homolog) position in each analysis

---

## Insights Gained

### Technical Insights
1. **PCA vs t-SNE:** [Compare linear vs non-linear methods]
2. **Information loss:** [How much variance was retained in 2D?]
3. **Interpretability:** [Which method was easier to understand biologically?]

### Biological Insights
1. **Transcription factor modules:** [Did similar TFs cluster together?]
2. **Network hubs:** [Which genes are structurally important?]
3. **Hidden genes:** [What important genes might be missed in 2D?]

### Methodological Insights
1. **Multi-view analysis:** Value of analyzing the same data from different perspectives
2. **Feature engineering:** How network features capture different information than raw data
3. **Validation:** Importance of biological knowledge in interpreting results

---

## Ethical Considerations

See [`ethical_reflection.md`](ethical_reflection.md) for detailed discussion of:

1. **Bias introduction through dimensionality reduction**
   - Variance-based bias (low-variance but critical genes)
   - Structural vs functional perspectives
   - Parameter sensitivity

2. **Visualization choices and interpretation**
   - The power and danger of 2D visualization
   - False cluster separation
   - Perceptual biases

3. **Diverse perspectives in feature selection**
   - Interdisciplinary collaboration
   - Multiple validation approaches
   - Transparent reporting

4. **Research equity and resource allocation**
   - Who benefits from simplified models?
   - Risk of overlooking important but "invisible" genes
   - Feedback loops in research funding

---

## Limitations

1. **Data limitations:**
   - Network from wild-type C. elegans only
   - May not generalize to stress conditions or mutants
   - Incomplete network (not all regulatory relationships are known)

2. **Method limitations:**
   - 2D reduction loses significant information
   - t-SNE stochastic (different runs may differ)
   - Parameter choices affect results

3. **Interpretation limitations:**
   - Correlation ≠ causation
   - Clusters may not have biological meaning
   - Need experimental validation

---

## Future Directions

1. **Technical improvements:**
   - Try other dimensionality reduction methods (UMAP, autoencoders)
   - Use more than 2 components for visualization
   - Ensemble methods combining multiple approaches

2. **Biological extensions:**
   - Integrate expression data from multiple conditions
   - Add functional annotations (GO terms, pathways)
   - Cross-species comparison

3. **Validation:**
   - Compare with known gene modules from literature
   - Experimental testing of predictions
   - Sensitivity analysis with different parameters

---

## References

*Add relevant papers and resources:*
- Original dataset source
- PCA and t-SNE methodology papers
- C. elegans gene regulation reviews
- Research ethics in computational biology

---

## Acknowledgments

- Course instructor and TAs
- Anthropic's Claude AI for guidance on conceptual understanding
- C. elegans research community for dataset

---

## Contact

Bell Jelly  
GitHub: [@bellajelly](https://github.com/bellajelly)

---

## License

This project is for educational purposes. Dataset used under original publication's terms.

