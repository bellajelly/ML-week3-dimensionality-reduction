# Ethical Reflection: Dimensionality Reduction in Gene Regulatory Networks

**Author:** Bell Jelly  
**Course:** Machine Learning - Week 3  
**Date:** February 2026

---

## Overview

This reflection explores the ethical implications of applying dimensionality reduction techniques (PCA and t-SNE) to biological data, specifically gene regulatory networks in *C. elegans*. Through this analysis, I examine how technical choices in feature reduction can introduce bias, affect interpretation, and potentially obscure biologically important information.

---

## 1. How Dimensionality Reduction Could Introduce Bias

### Information Loss and Selective Visibility

**Variance-based bias:**
- PCA prioritizes features with high variance, but what about genes that are:
  - Consistently important across conditions (low variance, high structural importance)?
  - Critical for network integrity but not highly expressed (high betweenness, low expression)?
- When we reduce 19,185 dimensions to 2, we retain only 24% of variance
- The remaining 76% might contain genes crucial for locomotion behavior and feeding behavior, which we are missing here

In my sleep research with C. elegans, genes involved in homeostatic regulation might show low variance because they're tightly controlled, but their dysregulation could be catastrophic. Dimensionality reduction might hide these "stable but essential" genes.

**Structural vs. Functional bias:**
- Option A (regulatory targets) reveals functional modules but might miss structural bottlenecks
- Option B (network topology) reveals hub genes but might miss co-regulated gene sets
- A gene like lin-42 appears differently in each view - which perspective is "correct"?

**Question to explore:** If we used these reduced dimensions to select genes for drug targets or genetic interventions, what critical genes might we miss?

---

## 2. How Visualization Choices Affect Interpretation

### The Power of 2D Projection

**Perceptual bias:**
- Humans are excellent at seeing clusters in 2D space, even when they might not be meaningful
- t-SNE can create "false" separation - clusters that look distinct might overlap in higher dimensions
- Distance between clusters in t-SNE has no meaning, but viewers naturally interpret proximity

**Parameter sensitivity:**
- How did choosing perplexity=30 affect t-SNE results?
- What if we used 2 vs 5 vs 10 principal components in PCA?
- Did standardization choices affect which features dominated?

**Color and scale choices:**
<img width="1789" height="1589" alt="image" src="https://github.com/user-attachments/assets/1a0cc82e-0a5c-49ca-89ee-ff0928cdb97d" />
Top: Dimensionality Reduction based on gene regulatory network comparison
Bottom: Dimensionality Reduction based on Network feature compariso

**If I showed only the PCA plot to a collaborator, they might see very little clusters, suggesting few variation. This could bias experimental design or funding decisions.

---

## 3. Network Resilience and Hidden Dependencies

### What Gets Lost When We Reduce Dimensions

**The "thalamus problem":**
Using my earlier analogy, genes with high betweenness centrality (like the thalamus in brain neural networks) might not have high variance across conditions, but their removal could fragment the network. Dimensionality reduction that prioritizes variance might render these genes invisible.

**Example scenarios:**
- A gene with low out-degree that connects two otherwise separate functional modules
- Compensatory mechanisms that only activate under stress (low variance in standard conditions)
- Redundant pathways that provide robustness (each pathway individually shows low importance)

**From my research:** 
In C. elegans sleep recovery, certain genes might show minimal expression changes but be critical for coordinating the recovery response. If we reduce dimensions based on differential expression alone, we lose these coordinators.

---

## 4. How Diverse Perspectives Could Improve Fairness

### Interdisciplinary Feature Selection

**The limitation of single metrics:**
- A computer scientist might prioritize computational efficiency (fewer features)
- A molecular biologist might prioritize functional annotation
- A systems biologist might prioritize network structure
- A clinician might prioritize drug targeting

**My proposal for improvement:**
1. **Multi-view dimensionality reduction:** Combine Option A and Option B simultaneously
   - Weight regulatory targets and network topology together
   - Use domain knowledge to set relative importance

2. **Transparent reporting:** Always show:
   - How much variance was retained
   - Which genes were lost in dimension reduction
   - Sensitivity analysis: do results change with different parameters?

3. **Biological validation:** 
   - Cross-reference with known disease genes
   - Check if "hidden" genes have documented importance in literature
   - Test predictions experimentally rather than relying solely on reduced-dimension visualization

**Diverse datasets:**
- This network comes from wild-type C. elegans under standard conditions
- What about mutant backgrounds? Stressed conditions? Different developmental stages?
- Biases in original data collection propagate through dimensionality reduction

---

## 5. Specific Ethical Concerns for Biological Data

### Research Equity

**Who benefits from simplified models?**
- Dimensionality reduction makes data more accessible to non-experts (positive)
- But oversimplification might lead to:
  - Premature clinical translation
  - Overlooking population-specific genetic variants
  - Reinforcing existing research biases (studying the same "visible" genes)

**Resource allocation:**
If funding decisions or drug development priorities are based on reduced-dimension "important genes," we risk:
- Missing therapeutic targets for rare conditions
- Overlooking genes that matter in specific populations but not in aggregate data
- Creating feedback loops where well-studied genes get more attention

### Reproducibility and Transparency

**The "black box" problem:**
- PCA is relatively interpretable (linear combinations)
- t-SNE is less interpretable (complex non-linear mapping)
- When papers show only the 2D visualization, readers can't assess what was lost

**My commitment:**
- Always report explained variance
- Provide supplementary data with full high-dimensional results
- Make code and parameters publicly available
- Acknowledge limitations explicitly

---

## 6. Recommendations for Ethical Practice

Based on this analysis, I propose these guidelines for using dimensionality reduction in biological research:

### Technical Practices

1. **Never use dimensionality reduction alone for feature selection**
   - Combine with domain knowledge
   - Validate "discarded" dimensions for biological importance
   - Use multiple reduction methods and compare

2. **Report comprehensively:**
   - Explained variance ratios
   - Sensitivity to parameter choices
   - Comparison with alternative methods
   - List of genes/features excluded

3. **Visualize uncertainty:**
   - Show confidence intervals if possible
   - Indicate which regions of 2D space are well-supported
   - Acknowledge when clusters might be artifacts

### Research Culture Practices

4. **Interdisciplinary review:**
   - Have biologists review computational reductions
   - Have computational scientists review biological interpretations
   - Include diverse expertise in peer review

5. **Open science:**
   - Deposit high-dimensional data publicly
   - Share code and exact parameters
   - Enable others to re-run with different choices

6. **Humility in interpretation:**
   - Acknowledge what's NOT visible in reduced dimensions
   - Resist the temptation to over-interpret clean clusters
   - Remember that absence of evidence is not evidence of absence

---

## 7. Personal Reflection

### What I Learned

Through this project, I came to appreciate that dimensionality reduction is not just a technical tool but an ethical choice. Every time we reduce dimensions, we make decisions about:
- What patterns matter
- What information can be discarded
- How we present findings to others

My neuroscience background helped me see parallels: just as brain lesion studies can be misleading about function (damage != function), dimensionality reduction can be misleading about importance (low variance != unimportant).

### Future Commitments

In my future work:
1. I will always examine what's lost, not just what's retained
2. I will validate computational reductions with biological knowledge
3. I will be transparent about methods and limitations
4. I will actively seek diverse perspectives in interpretation

---

## References


Claude AI
Google Collab
Kaggle Dataset: uploaded to Github
---

