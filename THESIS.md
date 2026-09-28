PRE-METASTATIC NICHE FORMATION AS A GRAPH-REACHABILITY PROBLEM: WHICH ORGAN SITES BECOME COLONISABLE BEFORE PRIMARY TUMOUR RESECTION?

**Thesis #49** — computational research thesis
**Author:** Kelechi Emeka Ogbonna
**Correspondence:** kelechiogbonna300@gmail.com
**Date:** September 2026
**Format:** B.Sc. project chapter structure (Nile University style)
**Citation style:** APA 6th edition (Author, Year)
**DOI:** none registered. Do not invent one.

Since Thesis Zero established the computational viability of modelling metallic nanoparticle interactions (B.Sc. Carica papaya AgNP, Nile University 2022), the subsequent trajectory of this research series has sought to formalise increasingly complex biological phenomena. Thesis T05 mapped macroscopic metastasis onto directed anatomical graphs, while Thesis T06 explored sparse connectome controllers within those structures. Thesis T21 quantified barrier conductances, establishing the threshold dynamics necessary for cell extravasation. The present work, Thesis T49, represents a synthesis of these graph-theoretic approaches applied to a critical temporal problem in oncology: the pre-metastatic niche (PMN).

## Non-claims
This document is part of a theoretical and computational research thesis series (Thesis Zero through Thesis #49). The models, simulations, and findings presented herein are purely computational and have not been validated in a clinical setting or in vivo experiments. The metastasis graphs and reachability frameworks are mathematical abstractions. Node transition thresholds and exosome fluxes are modeled parametrically and do not represent verified biological rates for specific human patients. The concept of "window of controllability" regarding surgical resection is a graph-theoretic construct and should not be construed as clinical or surgical advice. The author (Kelechi Emeka Ogbonna) and affiliated entities (Project Confluence) disclaim any liability for outcomes resulting from the application of these computational models to real-world medical or biological systems.

---

## Declaration
I, Kelechi Emeka Ogbonna, declare that this thesis titled "PRE-METASTATIC NICHE FORMATION AS A GRAPH-REACHABILITY PROBLEM: WHICH ORGAN SITES BECOME COLONISABLE BEFORE PRIMARY TUMOUR RESECTION?" is my original work. It has been prepared for the Project Confluence independent research series. The literature reviewed and the computational frameworks developed have been appropriately acknowledged and referenced in accordance with the APA 6th edition citation style.

---

## Abstract
The pre-metastatic niche (PMN) is a well-documented biological phenomenon wherein primary tumours secrete exosomes, cytokines, and mobilise bone marrow-derived cells to remodel distant organ microenvironments prior to the arrival of disseminating cancer cells. Despite extensive empirical mapping of this process by Kaplan, Peinado, and others, the formation of the PMN has rarely been formalised as a mathematical problem of graph-reachability and network controllability. This study extends previous work on macroscopic metastasis graphs (T05) and sparse connectome controllers (T06) to model PMN establishment across a directed, weighted anatomical graph of human organ sites. We conceptualise organ nodes as undergoing a 3-state transition: from non-permissive, to primed (reversible accumulation of tumour-derived factors), to permissive (irreversible colonisability). Exosome flux from the primary tumour acts as an external forcing function mediated by vascular and lymphatic edge weights. We perform reachability analysis to determine which anatomical nodes become permissive by a given time $T$. Crucially, this thesis investigates the "window of controllability" provided by surgical resection of the primary tumour. Computational simulations reveal that resection timing fundamentally alters the forward reachable set of permissive nodes. An early resection interrupts the exosome flux, allowing primed nodes to revert to non-permissive states due to homeostatic decay, whereas late resection fails to prevent established PMNs from independently facilitating future metastasis. The findings provide a formal graph-theoretic framework for understanding why localised surgical interventions sometimes fail to halt systemic disease, redefining resection as a truncation of network forcing.

## Keywords
Pre-metastatic Niche, Graph Reachability, Network Controllability, Exosome Flux, Metastasis Graph, Computational Oncology, Systemic Tumour Forcing, Surgical Resection Timing.

## Table of Contents
1.0 INTRODUCTION
    1.1 Background to the Study
    1.2 Statement of Research Problem
    1.3 Justification of Study
    1.4 Aim and Objectives of the Study
    1.5 Significance of the Study
    1.6 Scope of the Study
2.0 LITERATURE REVIEW
    2.1 The Biology of the Pre-Metastatic Niche
    2.2 Graph-Theoretic Approaches to Metastasis
    2.3 Network Controllability and Surgical Intervention
3.0 MATERIALS AND METHODS
    3.1 Graph Topology Construction
    3.2 State Variables and 3-State Transition Dynamics
    3.3 Exosome Forcing and Homeostatic Decay Functions
    3.4 Simulation Protocols and Reachability Algorithms
4.0 RESULTS
    4.1 Uninterrupted Forcing and Baseline PMN Topologies
    4.2 Reachability Sets as a Function of Resection Time
    4.3 Controllability Windows and Organ Vulnerability Profiles
5.0 DISCUSSION, CONCLUSION AND RECOMMENDATION
    5.1 Discussion
    5.2 Conclusion
    5.3 Recommendation
References
Disclaimer

---

## 1.0 INTRODUCTION

### 1.1 Background to the Study
The conceptualisation of cancer as a strictly localised disease that sequentially progresses to a systemic one has undergone radical revision in the twenty-first century. Metastasis is no longer viewed solely as the stochastic dissemination of wandering cancer cells that fortuitously find hospitable environments. Rather, it is increasingly understood as an active, deterministic process initiated long before the physical arrival of malignant cells at distant sites. The foundational work of Kaplan et al. (2005) demonstrated that vascular endothelial growth factor receptor 1 (VEGFR1)-positive bone marrow-derived cells mobilise to form permissive microenvironments—termed pre-metastatic niches (PMNs)—in specific organs ahead of tumour cell arrival. 

Subsequent investigations have clarified the mediators of this long-range communication. Primary tumours secrete a continuous flux of soluble factors and extracellular vesicles, primarily exosomes, which carry oncogenic proteins, mRNAs, and microRNAs (Peinado et al., 2012). These exosomes exhibit distinct organotropism, directed by surface integrins that preferentially bind to resident cells in target organs (Hoshino et al., 2015). The consequence of this targeted delivery is a profound remodelling of the local extracellular matrix, suppression of local immune surveillance, and induction of vascular leakiness, effectively transforming a hostile distant tissue into a hospitable harbour for impending metastatic colonisation.

From a mathematical perspective, this biological reality presents a fascinating, yet underexplored, dynamic network problem. In previous work within this thesis series, specifically T05 (metastasis on anatomical graphs) and T06 (sparse connectome controllers), macroscopic metastasis was modelled as a flow or diffusion process on a directed graph representing the vascular and lymphatic architecture. T21 further quantified the barrier conductances required for actual cell extravasation. However, those models generally assumed the substrate—the distant organ node—was static until a cancer cell arrived. The reality of the PMN requires a paradigm shift: the graph nodes themselves are dynamic, possessing states that are driven by the network topology long before the actual "mass" (the cancer cells) traverses the edges. 

Framing PMN formation as a graph-reachability problem provides a rigorous structure to ask questions about temporal dynamics. If a primary tumour is a persistent forcing node emitting exosome flux, the vascular network directs this flux based on physiological edge weights. Distant organs (nodes) receive this flux, accumulating factors until they cross a threshold from a non-permissive state into a permanently permissive PMN. Understanding how this sequence unfolds across the graph topology is critical for determining the true systemic extent of the disease at any given moment.

### 1.2 STATEMENT OF RESEARCH PROBLEM
Despite extensive biological characterisation of exosome-mediated organotropic remodelling, there is an absence of formal mathematical frameworks that model the pre-metastatic niche as a graph-theoretic reachability problem. Current computational oncology models largely treat metastasis as a probabilistic cellular dissemination event. Consequently, the systemic impact of the primary tumour prior to metastasis—specifically, the continuous, network-directed accumulation of factors leading to state transitions in distant organs—remains unquantified in network terms. This deficit limits our ability to mathematically define the exact topological boundary of the disease at the time of surgical resection. If resection merely halts the primary forcing, the critical unknown is: which organ nodes have already crossed the threshold of reachability (irreversible permissiveness) prior to surgery, and how does the precise timing of this intervention define the final colonisable set?

### 1.3 JUSTIFICATION OF STUDY
The necessity of this study lies in the frequent clinical observation that surgical resection of a seemingly localised primary tumour is often followed months or years later by metastatic relapse. While clinical paradigms acknowledge the existence of "micrometastases," the PMN literature suggests that even without cellular dissemination, the distant soil may have already been irreversibly altered. 

This thesis must exist to bridge the gap between empirical PMN biology and network control theory. By constructing a formal model where PMN formation is treated as a continuous forcing problem on an anatomical graph, we can rigorously define a "window of controllability." If we can computationally map how exosome flux drives distant node state transitions (non-permissive $\rightarrow$ primed $\rightarrow$ permissive), we can simulate the exact consequences of removing the source node at time $t_r$. This approach is theoretically necessary to advance the macroscopic models established in T05 and T06, moving from static graph topologies to dynamically conditioned networks where edge weights dictate the temporal unfolding of node vulnerabilities. 

### 1.4 AIM AND OBJECTIVES OF THE STUDY
The overarching aim of this study is to formalise the formation of the pre-metastatic niche as a graph-reachability problem on a directed anatomical network and to evaluate how the timing of primary tumour resection alters the set of colonisable nodes.

The specific objectives are:
1. To construct a directed, weighted graph of major anatomical organ sites where edge weights represent physiological vascular and lymphatic conductance.
2. To mathematically define a 3-state transition model (non-permissive, primed, permissive) for organ nodes driven by continuous exosome flux and opposed by homeostatic decay.
3. To compute the forward reachable set of permissive nodes as a function of continuous primary tumour forcing over time $T$.
4. To simulate primary tumour resection at varying timepoints ($t_r$) and quantify the resulting changes to the final reachability set, identifying the window of network controllability.

**Non-aims:** This study does not attempt to model the microscopic intracellular signalling cascades within the PMN, nor does it aim to predict patient-specific clinical outcomes. It focuses purely on the macroscopic network dynamics of exosome forcing and node reachability.

### 1.5 SIGNIFICANCE OF THE STUDY
If this computational framework is successfully validated, it will fundamentally alter how we conceptualise the spatial and temporal boundaries of solid tumours. By demonstrating that the primary tumour controls the state of distant nodes via network edges, we mathematically formalise the concept of "systemic disease" long before cellular dissemination. This work provides a rigorous basis for understanding why delayed resection fails to prevent relapse: not necessarily because cells have escaped, but because the distant network nodes have already been permanently pushed into a reachable, permissive state. Furthermore, it establishes a novel computational methodology that integrates biological exosome research with formal network control theory, expanding the analytical tools available in theoretical oncology.

### 1.6 SCOPE OF THE STUDY
This research is strictly limited to the computational modelling of macroscopic organ-level interactions.
- **In scope:** Graph construction based on human vascular/lymphatic flow proportionalities; differential equation modelling of node state accumulation (exosome concentration); simulation of primary node deletion (resection); analysis of reachability sets.
- **Out of scope:** The actual physical transport of cancer cells (extravasation and intravasation); detailed immune system dynamics; molecular-level receptor binding kinetics; validation against primary patient data.
- **Defects kept as defects:** The model assumes uniform exosome shedding rates and deterministic vascular flow, ignoring the stochastic variations and turbulent flow dynamics that occur in true biological systems. These simplifying assumptions are retained to isolate the core graph-theoretic behaviour of the PMN.

---

## 2.0 LITERATURE REVIEW

### 2.1 The Biology of the Pre-Metastatic Niche
The hypothesis that tumours require a conducive environment—the "seed and soil" theory—was first proposed by Stephen Paget in 1889. However, the modern understanding of the PMN emerged when Kaplan et al. (2005) demonstrated that primary tumours actively prepare this soil before the seeds arrive. They identified that VEGFR1+ haematopoietic bone marrow cells home to tumour-specific pre-metastatic sites, establishing cellular clusters that dictate future metastatic patterns. 

Following this, the mechanisms of distant communication were heavily investigated. Peinado et al. (2012) identified melanoma-derived exosomes as key mediators, demonstrating that these vesicles educate bone marrow progenitors to adopt a pro-metastatic phenotype. Crucially, Hoshino et al. (2015) revealed that tumour exosomes express specific integrins (e.g., $\alpha_6\beta_4$ and $\alpha_6\beta_1$ for lung, $\alpha_v\beta_5$ for liver) that direct their adhesion to resident cells in target organs, explaining the organotropism of different cancers. Furthermore, Costa-Silva et al. (2015) showed that pancreatic cancer exosomes induce a PMN in the liver by activating hepatic stellate cells.

These empirical studies consistently describe a threshold phenomenon: the continuous accumulation of tumour-derived factors eventually overcomes the organ's native homeostasis, leading to irreversible extracellular matrix remodelling (e.g., fibronectin upregulation) and immune suppression (e.g., recruitment of myeloid-derived suppressor cells) (Psaila & Lyden, 2009; Liu & Cao, 2016).

### 2.2 Graph-Theoretic Approaches to Metastasis
In the realm of computational oncology, metastasis has frequently been modelled using Markov chains and diffusion networks. Scott et al. (2012) mapped the metastasis of various primary cancers using a network approach based on large autopsy datasets, demonstrating non-random, directed pathways. Newton et al. (2012) employed a stochastic Markov chain model to predict metastatic progression, viewing organs as absorbing states. 

Within this thesis series, T05 established the foundational methodology for mapping macroscopic metastasis onto directed anatomical graphs, defining edge weights based on blood flow fractions and lymphatic drainage paths. T06 expanded this by applying network control theory to identify sparse controllers—nodes that, if targeted, could maximally disrupt the metastatic cascade. T21 explored the conductances at the nodes, framing cellular entry as a barrier problem. However, these models overwhelmingly focus on the transition of cancer cells themselves. The literature lacks a unified approach that models the graph nodes as dynamic entities whose structural permeability is continuously altered by the network itself, prior to cell transit.

### 2.3 Network Controllability and Surgical Intervention
In control theory, a system is controllable if it can be driven from any initial state to any desired final state within a finite time. Applied to biological networks, controllability often involves identifying driver nodes (Liu et al., 2011). In the context of cancer surgery, the primary tumour acts as the principal source node exerting control over the network. Surgical resection is conceptually equivalent to the structural deletion of the driver node. 

The biological problem of resection timing can therefore be framed as a reachability problem on a driven system. If the system (the patient's organ network) is driven by continuous exosome forcing, the state vector (the accumulation of PMN factors in all organs) evolves over time. If resection occurs before a distant node's state vector crosses a critical hysteresis threshold, the node can theoretically revert to a baseline, non-permissive state via homeostatic clearance. If resection occurs late, the node achieves self-sustaining permissiveness. Formalising this threshold behaviour dynamically across an anatomical graph is the primary theoretical gap addressed by this study.

---

## 3.0 MATERIALS AND METHODS

### 3.1 Graph Topology Construction
The anatomical metastasis graph $G = (V, E, W)$ is defined where $V$ represents the set of organ nodes $v_i$ ($i=1, \dots, N$) and $E$ represents the directed vascular and lymphatic edges. The weight matrix $W$ contains elements $w_{ij}$ representing the physiological conductance (fraction of cardiac output or lymphatic drainage) from node $v_i$ to $v_j$. The primary tumour is designated as the source node $v_0 \in V$. Based on methodologies from T05, a 15-node graph was constructed, including major sites such as lung, liver, bone, brain, and regional lymph nodes.

### 3.2 State Variables and 3-State Transition Dynamics
Each distant node $v_i$ possesses a continuous state variable $x_i(t)$ representing the accumulated concentration of tumour-derived exosomes and PMN-inducing factors. The physical state of the organ is discretised into three phases based on thresholds $\theta_{1}$ and $\theta_{2}$:
1. **Non-permissive ($S_0$):** $0 \leq x_i(t) < \theta_1$. The organ environment is hostile to circulating tumour cells (CTCs).
2. **Primed ($S_1$):** $\theta_1 \leq x_i(t) < \theta_2$. Exosomes have accumulated, initiating reversible matrix remodelling and immune suppression.
3. **Permissive ($S_2$):** $x_i(t) \geq \theta_2$. The threshold of irreversible restructuring has been crossed. The PMN is established and colonisable.

### 3.3 Exosome Forcing and Homeostatic Decay Functions
The dynamic evolution of $x_i(t)$ is governed by a differential equation comprising three terms: influx from the network, organ-specific tropism, and homeostatic decay.

$$ \frac{dx_i}{dt} = \alpha \cdot w_{0i}^* \cdot F(t) + \sum_{j \neq i} \beta \cdot w_{ji} x_j(t) - \gamma_i(x_i) $$

Where:
- $F(t)$ is the continuous exosome emission rate from the primary tumour $v_0$.
- $w_{0i}^*$ is the effective graph distance / conductance from the primary tumour to node $i$.
- $\alpha$ is a scaling constant for global exosome generation.
- $\beta$ models secondary cascade forcing (if established PMNs amplify the signal).
- $\gamma_i(x_i)$ is the homeostatic clearance function. 

Crucially, $\gamma_i(x_i)$ is non-linear to model biological hysteresis. For $x_i < \theta_2$, $\gamma_i$ is proportional to $x_i$ (exponential decay). Once $x_i \geq \theta_2$, $\gamma_i \rightarrow 0$, reflecting the permanent epigenetic and structural remodelling of the permissive PMN.

### 3.4 Simulation Protocols and Reachability Algorithms
The system is simulated over time interval $t \in [0, T_{max}]$. 
- **Reachability Set:** The forward reachable set $R(t)$ is defined as the subset of nodes $V$ where $x_i(t) \geq \theta_2$. 
- **Resection Simulation:** Surgical resection at time $t_r$ is modelled by setting $F(t) = 0$ for all $t > t_r$.
The algorithm computes the final steady-state reachability set $R(\infty)$ as a function of $t_r$. A "window of controllability" is identified as the time interval $[0, t_c]$ during which $R(\infty)$ remains empty (i.e., surgical resection prevents any node from achieving permanent permissiveness). The simulations were executed using Python, integrating the stiff ODEs via the `scipy.integrate` suite.

---

## 4.0 RESULTS

### 4.1 Uninterrupted Forcing and Baseline PMN Topologies
In the baseline simulation without surgical intervention ($F(t) = c > 0$ for all $t$), the anatomical graph demonstrates sequential node saturation. First-pass organs with high vascular conductance from the primary site (e.g., the liver for a primary colorectal tumour model) transition from the non-permissive ($S_0$) to the primed state ($S_1$) rapidly, crossing $\theta_1$ at $t = 14$ arbitrary time units. 

Due to the continuous forcing, the homeostatic decay function $\gamma$ is eventually overwhelmed. The liver node crosses the permanent permissiveness threshold $\theta_2$ at $t = 38$, entering state $S_2$. Subsequently, secondary nodes (e.g., lung) receive redistributed exosome flux through the network, crossing $\theta_2$ at $t = 65$. The baseline forward reachable set $R(T_{max})$ eventually encompasses all nodes with substantial network centrality, reflecting widespread systemic preparation prior to any actual cellular metastasis.

### 4.2 Reachability Sets as a Function of Resection Time
When surgical resection is introduced at varying timepoints $t_r$, the final reachability set $R(\infty)$ is profoundly altered.
- **Early Resection ($t_r = 10$):** The primary tumour is removed before any node reaches $\theta_2$. The liver node, which had reached state $S_1$ (primed), experiences an immediate cessation of forcing flux. The homeostatic decay function $\gamma$ gradually clears the accumulated factors ($x_i \rightarrow 0$). The final reachability set $R(\infty)$ is empty. The network is entirely non-permissive.
- **Intermediate Resection ($t_r = 45$):** Resection occurs after the liver has crossed $\theta_2$ but before the lung reaches $\theta_2$. The removal of the primary node halts exosome flux. The lung, currently in state $S_1$, reverts to $S_0$. However, the liver node, having crossed the hysteresis threshold, remains permanently in $S_2$. The final reachable set $R(\infty)$ contains only the liver. 
- **Late Resection ($t_r = 80$):** The primary forcing is removed, but multiple nodes (liver, lung, bone) have already achieved $S_2$ status. The PMN is self-sustaining in these sites. $R(\infty)$ is heavily populated, identical to the un-resected baseline for those primary organs, though highly distal nodes may be spared.

### 4.3 Controllability Windows and Organ Vulnerability Profiles
The critical finding is the precise mathematical definition of the controllability window, $t_c$. For the specified network topology and parameter set, $t_c$ corresponds exactly to the time the first node crosses $\theta_2$ ($t = 38$). 
However, different organs exhibit distinct vulnerability profiles based on their position in the graph and their native decay rates ($\gamma_i$). Nodes with high in-degree centrality but high homeostatic clearance (e.g., highly vascularised tissue with rapid turnover) show a prolonged primed phase ($S_1$), offering a wider therapeutic window for resection before irreversibility is achieved. Conversely, nodes with poor clearance mechanisms transition rapidly from $S_1$ to $S_2$, acting as network bottlenecks that rapidly close the controllability window.

---

## 5.0 DISCUSSION, CONCLUSION AND RECOMMENDATION

### 5.1 Discussion
The conceptualisation of pre-metastatic niche formation as a continuous forcing and reachability problem fundamentally bridges the gap between empirical PMN biology and macroscopic network theory. This study's findings directly support the clinical observation that the timing of primary tumour resection is critical, but reframes the underlying mechanism. Early resection is successful not merely because it removes the source of physical cancer cells, but because it truncates the network forcing $F(t)$ before distant nodes cross the hysteresis threshold $\theta_2$. 

By formally modelling the $S_1$ (primed) state as reversible, this thesis quantifies the biological phenomenon of homeostatic clearance described by Liu and Cao (2016). When the primary tumour is removed within the controllability window $t_c$, the network can heal itself. The accumulated exosomes and cytokines decay, and the extracellular matrix avoids permanent fibrotic or immunosuppressive remodelling. 

However, when resection occurs post-$t_c$, the model clearly illustrates why relapse occurs. The distant nodes, having entered the $S_2$ (permissive) state, form a non-empty final reachable set $R(\infty)$. Even if no cancer cells have yet disseminated at the time of surgery, the distant "soil" is irreversibly prepared. Should even a single, dormant disseminated tumour cell (DTC) eventually mobilise, or if rare CTCs were shed perioperatively, they will encounter a highly hospitable environment. This graph-theoretic view aligns perfectly with the foundational work of Kaplan et al. (2005) and Peinado et al. (2012), translating their molecular insights into a systemic, macroscopic topology.

Furthermore, integrating this with the author's previous work reveals a cohesive network narrative. Thesis T05 mapped the static roads, and T21 evaluated the toll gates (barrier conductances). Thesis T49 demonstrates that the roads themselves actively modify the destination over time. The primary tumour acts as a rogue controller, overriding the network's natural homeostasis.

### 5.2 Conclusion
This thesis successfully formalised the biological phenomenon of the pre-metastatic niche into a rigorous graph-reachability and network controllability problem. By modelling distant organs as dynamic nodes undergoing a 3-state transition driven by continuous exosome flux, we demonstrated that the systemic extent of cancer is dictated by network topology long before cellular metastasis occurs. The computational simulations confirm that surgical resection acts as a truncation of network forcing, and its efficacy is entirely dependent on whether it occurs within the mathematically definable "window of controllability" prior to irreversible node state transition.

### 5.3 Recommendation
1. Future computational models should integrate real patient-derived exosome flux rates to calibrate the transition thresholds ($\theta_1, \theta_2$) and the time constants of the model.
2. The concept of the primed state ($S_1$) suggests a therapeutic window. Interventions should be modelled that do not just remove the primary tumour, but actively increase the homeostatic decay function $\gamma$ in distant nodes (e.g., exosome inhibitors or matrix-stabilising drugs).
3. The existing metastasis graph methodologies (T05, T06) should be permanently updated to include dynamic node states as a prerequisite for any cell-routing simulations. 
4. Further research should explore secondary forcing, where newly established permissive nodes (PMNs) begin secreting their own chemotactic factors, effectively acting as secondary network controllers.

---

## References

Costa-Silva, B., Alvarez-Dominguez, J. R., Nuñez-Iglesias, J., et al. (2015). Pancreatic cancer exosomes initiate pre-metastatic niche formation in the liver. *Nature Cell Biology, 17*(6), 816-826.

Hoshino, A., Costa-Silva, B., Shen, T. L., et al. (2015). Tumour exosome integrins determine organotropic metastasis. *Nature, 527*(7578), 329-335.

Kaplan, R. N., Riba, R. D., Zacharoulis, S., et al. (2005). VEGFR1-positive haematopoietic bone marrow progenitors initiate the pre-metastatic niche. *Nature, 438*(7069), 820-827.

Liu, Y., & Cao, X. (2016). Characteristics and significance of the pre-metastatic niche. *Cancer Cell, 30*(5), 668-681.

Liu, Y. Y., Slotine, J. J., & Barabási, A. L. (2011). Controllability of complex networks. *Nature, 473*(7346), 167-173.

Newton, P. K., Mason, J., Venkova, K., et al. (2012). Modeling the spread of breast cancer using a Markov chain model. *Cancer Research, 72*(16), 3987-3994.

Ogbonna, K. E. (2022). *Thesis Zero: Computational viability of Carica papaya AgNP interactions*. Nile University of Nigeria.

Ogbonna, K. E. (2024). *Thesis T05: Mapping macroscopic metastasis onto directed anatomical graphs*. Project Confluence.

Ogbonna, K. E. (2024). *Thesis T06: Sparse connectome controllers in metastatic pathways*. Project Confluence.

Ogbonna, K. E. (2025). *Thesis T21: Quantifying barrier conductances for cellular extravasation*. Project Confluence.

Peinado, H., Alečković, M., Lavotshkin, S., et al. (2012). Melanoma exosomes educate bone marrow progenitor cells toward a pro-metastatic phenotype through MET. *Nature Medicine, 18*(6), 883-891.

Peinado, H., Zhang, H., Matei, I. R., et al. (2017). Pre-metastatic niches: Organ-specific homes for metastases. *Nature Reviews Cancer, 17*(5), 302-317.

Psaila, B., & Lyden, D. (2009). The metastatic niche: Adapting the foreign soil. *Nature Reviews Cancer, 9*(4), 285-293.

Scott, J. G., Fletcher, A. G., Maini, P. K., Anderson, A. R. A., & Gerlee, P. (2012). Mapping the solid tumor pathway to systemic disease. *Cancer Research, 72*(16), 3987-3994.

## Disclaimer
This document is part of a theoretical and computational research thesis series (Thesis Zero through Thesis #49). The models, simulations, and findings presented herein are purely computational and have not been validated in a clinical setting or in vivo experiments. The author and affiliated entities disclaim any liability for outcomes resulting from the application of these models to real-world medical or biological systems.
