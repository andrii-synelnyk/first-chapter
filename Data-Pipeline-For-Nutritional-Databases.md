# Building an Optimized Data Pipeline for Crowdsourced Nutritional Databases with Incremental Updates

## Chapter 1: Introduction
### 1.1 Background and Context

In recent years, data engineering has become a cornerstone of modern information systems, enabling organizations to collect, transform, and analyze massive volumes of data efficiently. The expansion of digital platforms and interconnected devices has accelerated the need for reliable data pipelines that can handle dynamic and heterogeneous datasets. Within this context, nutritional databases represent a critical domain where data integrity and accessibility directly influence public health awareness and consumer decision-making.

Crowdsourced nutritional platforms such as OpenFoodFacts or Yuka have emerged as key initiatives that democratize access to food product information. They aggregate data provided by volunteers and consumers, forming extensive repositories of nutritional facts, ingredient lists, and ecological indicators. However, the open and distributed nature of crowdsourced data introduces challenges concerning accuracy, completeness, consistency, and update frequency. To maintain credibility and usability, these systems must implement sophisticated engineering pipelines that continuously validate, clean, and enrich incoming data.

Advancements in cloud computing and machine learning have transformed the way such data pipelines are designed and maintained. Cloud-native environments provide scalable and cost-efficient infrastructures for storing and processing large datasets, while machine learning algorithms offer automated means of improving data quality, for instance by predicting missing product categories or identifying anomalies. The synergy between these two domains—data engineering and artificial intelligence—forms the technological foundation of this thesis.

### 1.2 Motivation and Problem Statement

Despite significant progress in crowdsourced data platforms, there remain persistent limitations that hinder their scalability and reliability. Many nutritional databases rely on bulk data refreshes, resulting in latency between the submission of new product information and its availability to end users. Furthermore, manual or semi-manual cleaning processes often lead to inconsistencies across records, while the lack of standardized category mappings complicates data analysis and machine learning applications.

This thesis addresses the problem of inefficient data processing and delayed updates in large-scale nutritional databases. The proposed solution is an optimized data pipeline capable of performing incremental updates—that is, ingesting only new or modified data instead of reprocessing the entire dataset. Incremental architectures drastically reduce computational overhead and enable near-real-time data synchronization. By integrating a predictive model for automatic category assignment, the system also mitigates issues related to incomplete or inconsistent labeling.

The motivation for this research stems from the increasing societal emphasis on nutritional transparency and data-driven health awareness. As consumers demand detailed, trustworthy, and up-to-date product information, data engineering systems must evolve to meet these expectations. Furthermore, scalable and automated data pipelines represent a broader industrial challenge that extends beyond the nutritional domain—covering retail analytics, environmental monitoring, and other sectors dependent on dynamic data streams.

In summary, although numerous studies have explored aspects of data ingestion, transformation, and storage, relatively few have focused on holistic, incremental, and ML-enhanced pipelines for crowdsourced databases. This thesis aims to fill that gap by proposing a practical yet extensible engineering framework addressing both data and infrastructure challenges.

### 1.3 Aim and Objectives

The main aim of this thesis is to design and implement an optimized data pipeline for crowdsourced nutritional databases that supports incremental updates, automated data enrichment, and scalable cloud deployment.

The specific objectives of the study are as follows:

- To develop a modular pipeline for the daily ingestion of product data from the OpenFoodFacts API.  
- To implement efficient data cleaning and transformation processes ensuring accuracy and standardization.  
- To integrate a machine learning model for predicting missing or inconsistent product categories.  
- To design a cloud-based architecture capable of handling incremental updates with minimal latency.  
- To develop and expose a RESTful API delivering the processed data to external applications, such as a mobile nutrition app.  
- To evaluate system performance in terms of processing speed, scalability, and data quality improvements.  

Together, these objectives define a comprehensive framework that bridges data engineering practices with intelligent automation, supporting continuous and reliable information delivery.

### 1.4 Scope of the Study

The study focuses exclusively on the software and data engineering aspects of nutritional information processing. It encompasses the design and evaluation of a backend pipeline, associated databases, and a machine learning component for data enrichment. The scope does not include hardware implementation or the full development of the consumer-facing mobile application, except for demonstrating integration through an API endpoint.

The system is constrained by publicly available data from the OpenFoodFacts API, which introduces potential variability in completeness and quality. Due to resource limitations, the machine learning model will be trained on a representative subset of the dataset rather than on all global entries. Cloud deployment will utilize Google Cloud Platform (GCP) services such as Cloud Storage, BigQuery, and Cloud Run, selected for their accessibility and alignment with the university’s available resources.

The research assumes a stable internet connection, consistent API availability, and access to sufficient computing resources for model training and testing. It does not address nutritional data verification or the creation of novel data collection mechanisms, as the focus remains on data processing efficiency and engineering optimization.

### 1.5 Thesis Structure

This thesis is organized into five chapters, each addressing a specific stage of the research and implementation process.

- **Chapter 1 – Introduction**  
  Provides the overall background, motivation, objectives, scope, and structure of the work. It establishes the engineering and scientific context that underpins the research problem and highlights the need for efficient, scalable, and intelligent data pipelines in the context of crowdsourced nutritional databases.

- **Chapter 2 – Literature Review and Theoretical Background**  
  Reviews previous studies and technologies related to data pipelines, incremental updates, and data engineering architectures. It also covers machine learning applications in data enrichment, existing open-source initiatives such as OpenFoodFacts, and recent advances in cloud-based orchestration frameworks. This chapter identifies current limitations in the field and positions the proposed solution within the broader academic and industrial landscape.

- **Chapter 3 – System Design and Methodology**  
  Describes the architecture and design choices for the proposed data pipeline. It details the stages of data ingestion, transformation, storage, machine learning integration, and API development. The chapter explains the technological stack, including programming languages, frameworks, and cloud services, and justifies their selection in terms of scalability, performance, and maintainability.

- **Chapter 4 – Implementation and Results**  
  Presents the practical realization of the system and the outcomes of testing and evaluation. It includes performance metrics such as ingestion time, processing latency, scalability under varying workloads, and the predictive accuracy of the machine learning model. The findings are analyzed and discussed in relation to the objectives and prior research.

- **Chapter 5 – Conclusions and Future Work**  
  Summarizes the main achievements of the project and reflects on their contribution to the field of data engineering. It also identifies the limitations encountered during implementation and proposes directions for future improvement, including expanding model capabilities, incorporating additional data sources, or transitioning toward real-time streaming architectures.

This structure provides a clear logical progression from conceptual foundations to technical implementation and evaluation, ensuring coherence and readability for the entire thesis.

### 1.6 Connection to the Scientific and Engineering Context

The proposed research is situated at the intersection of data engineering, cloud computing, and applied machine learning, fields that have experienced substantial scientific and industrial growth in the last decade. Data engineering serves as the backbone of modern analytics systems, enabling organizations to transform raw data into structured insights. According to Giebler et al. (2020), the efficiency of these systems depends largely on the reliability and automation of their underlying pipelines.

Incremental data processing represents a particularly active research area. Traditional batch processing methods, while simple, often result in redundant computations and delayed availability of results. Studies such as Borkar et al. (2015) and Khandelwal et al. (2019) highlight that incremental architectures can significantly reduce processing overhead and latency, making them ideal for continuously updated datasets. This concept aligns closely with the requirements of crowdsourced nutritional databases, where thousands of product entries are modified daily.

From an artificial intelligence perspective, machine learning techniques contribute to data enrichment and validation by automating classification, anomaly detection, and missing-value prediction. For instance, Zhou et al. (2021) demonstrated that supervised learning algorithms can accurately categorize unlabelled items in large datasets, thereby enhancing usability without extensive manual intervention. Integrating such algorithms directly within a data pipeline reduces the need for external preprocessing steps and enables continuous improvement of data quality.

The adoption of cloud-native infrastructures has further transformed the scalability and maintainability of data systems. Platforms such as Google Cloud Platform (GCP), Amazon Web Services (AWS), and Microsoft Azure provide managed services for storage, orchestration, and deployment that support elastic scaling and resource optimization. Tools like Apache Airflow and Prefect facilitate workflow automation and monitoring, while containerization technologies such as Docker and Kubernetes ensure portability and resilience. The convergence of these tools underpins modern engineering solutions for data-intensive applications.

In the context of public health and nutrition, the availability of structured, high-quality product data has tangible societal benefits. Research by Drewnowski et al. (2022) emphasizes that accessible nutritional information can influence consumer behavior and support healthier dietary choices. Therefore, improving the technological infrastructure behind such data sources directly contributes to global efforts in promoting transparency and well-being.

This thesis builds upon these scientific foundations by uniting the principles of data engineering, machine learning, and cloud computing into an integrated pipeline designed for incremental, high-quality updates. It contributes not only a functional system but also a methodological framework that can be adapted to other domains requiring frequent data synchronization and enrichment.

### 1.7 Summary

Chapter 1 has introduced the conceptual basis and rationale for developing an optimized data pipeline tailored to crowdsourced nutritional databases. The discussion outlined the significance of reliable data processing within the modern digital ecosystem, identified existing shortcomings in current approaches, and formulated specific objectives addressing these gaps. The chapter also delimited the scope of the work, clarified methodological assumptions, and situated the research within contemporary scientific developments in data engineering and machine learning.

The following chapters will expand upon these foundations. Chapter 2 will provide a critical overview of the literature and theoretical models underpinning incremental data processing and intelligent data pipelines. Chapter 3 will describe the design and architecture of the proposed system, while Chapter 4 will demonstrate its implementation and empirical results. Finally, Chapter 5 will summarize the main findings, evaluate their broader implications, and suggest potential avenues for future enhancement.
