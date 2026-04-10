
# Thesis Research: Hybrid Human-LLM Propaganda Detection

### **1. Framework Overview**
The framework presents a **hybrid annotation system** designed to address the challenges of detecting propaganda in short-form social media text (specifically Russian propaganda from the HQP dataset). It integrates **LLM pre-annotation** (acting as a "weak labeler") with **human intelligence** to improve scalability and consistency.

### **2. Hierarchical Propaganda Taxonomy**
To reduce cognitive load on annotators, the 14 fine-grained techniques from Martino et al. (2020) are organized into **three coarse-grained categories** based on rhetorical function:
*   **(A) Emotional Appeals**: Techniques designed to trigger immediate emotional responses.
*   **(B) Simplification and Distortion**: Methods like **repetition**, **exaggeration/minimization**, **black-and-white fallacy**, and **thought-terminating clichés** that oversimplify complex issues.
*   **(C) Manipulating Trust, Authority, and Rational Discourse**: Includes **doubt**, **appeal to authority**, **whataboutism/straw man/red herring**, and **bandwagon/reductio ad hitlerum**.

### **3. The Human Bottleneck (Study 1)**
*   **Subjectivity**: Purely human annotation is difficult because propaganda exploits cognitive biases and is highly dependent on cultural/linguistic context.
*   **Agreement Gap**: While humans agree moderately on the **3 broad categories (88.45% consensus)**, agreement drops significantly for the **14 fine-grained techniques (47.61% consensus)**.
*   **Inefficiency**: Manual annotation is time-consuming, averaging **151.70 seconds per tweet**.

### **4. LLM Pre-Annotation Pipeline**
Using Llama3-70B, the pipeline follows four specific steps:
1.  **Extraction**: Identify specific words or text spans indicating propaganda.
2.  **Explanation**: Generate a logical justification for why each span is considered propagandistic.
3.  **Local Labeling**: Assign a fine-grained label to each specific span.
4.  **Global Labeling**: Assign a single representative label for the entire tweet.

### **5. Key Insights & Findings**
*   **Multi-Label Reality**: Most propagandistic tweets are not limited to a single technique; they typically contain **multiple propagandistic segments**, making global labels alone insufficient.
*   **Geometry vs. Intent**: LLMs are proficient at identifying the **"geometry"** (linguistic/rhetorical patterns) of propaganda but often fail to capture **intent**. They may misflag "anti-Western criticism" in normal political discourse as propaganda because it shares the same rhetorical structure.
*   **Efficiency Gains**: Providing humans with LLM pre-annotations (Study 2) reduced annotation time by nearly **73% (down to 41.14 seconds)** and significantly increased the inter-annotator agreement (Krippendorff’s Alpha rose from ~0.12 to ~0.59).
*   **Teacher-Student Pipeline**: Knowledge distillation allows a **70B "Teacher" model** to train **3B or 8B "Student" models**. While student models are effective at span detection, they are less certain about assigning specific fine-grained local labels due to label overlap and limited data.

### **6. Critical Considerations for Thesis**
*   **Weak Categorization**: LLM outputs should be treated as **"weak labels"** or suggestions to assist humans, rather than definitive classifications.
*   **Automation Bias**: There is a risk that human annotators might over-rely on LLM suggestions, potentially reducing their own critical thinking.
*   **Ethical Warning**: LLMs may inherit **geopolitical and socioeconomic biases** from their training data, which can influence their labeling of sensitive political content.
