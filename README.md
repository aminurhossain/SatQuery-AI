# SatQuery AI: An Interactive Vision-Language Assistant for Multimodal Remote Sensing Image Analysis through Text Queries

**Category:** Software[cite: 1]  
**Theme:** Space Technology[cite: 1]  
**Organization:** Space Applications Centre (SAC), ISRO, Department of Space[cite: 1]  
**Mentors:** Md Aminur Hossain, Sanjay K Singh, S Devakanth Naidu[cite: 1]  
**Contact:** aminur@sac.isro.gov.in, md.aminurhossain@gmail.com[cite: 1]

---

## 1. Background

Remote-sensing imagery is widely used for agricultural monitoring, disaster management, urban planning, forest monitoring, water-resource assessment, infrastructure mapping, and environmental analysis[cite: 1]. However, most existing remote-sensing AI solutions are developed as isolated applications for a single predefined task, such as land-cover classification, object detection, visual question answering, or change detection[cite: 1]. These systems often require users to understand satellite-data characteristics, GIS workflows, model selection, and task-specific parameters[cite: 1]. Consequently, non-expert users may find it difficult to obtain meaningful information from satellite imagery through simple natural-language queries[cite: 1].

Many operational remote-sensing questions cannot always be answered reliably using a single optical image[cite: 1]. Relevant information may be distributed across paired or multiple observations acquired at different times or by different sensors[cite: 1]. Optical and multispectral imagery provides spectral and contextual information, whereas synthetic aperture radar (SAR) provides complementary structural information and supports day-and-night acquisition through cloud cover[cite: 1]. Multitemporal image pairs are required to identify and interpret changes over time, while co-registered optical-SAR pairs can provide more complete and reliable information than either modality alone[cite: 1].

A general-purpose large language model (LLM) or vision-language model (VLM) cannot be expected to perform these specialised tasks reliably without adaptation to remote-sensing imagery, sensor characteristics, and domain-specific terminology[cite: 1]. The proposed solution must therefore include remote-sensing fine-tuning or domain adaptation and may employ multiple specialised models for different tasks[cite: 1]. `BigEarthNet.txt` will serve as the primary dataset for adapting image-text representations to multisensor remote-sensing data[cite: 1]. `VRSBench` and `RSVQA` will be used to evaluate single-image captioning, grounding, and visual question answering, while `CDVQA` will be used to evaluate multitemporal change-based visual question answering[cite: 1].

The novelty of SatQuery AI lies in its agentic, query-driven framework[cite: 1]. Instead of applying a single generic VLM, the system selects and executes suitable remote-sensing specialist models, validates inputs, combines their outputs, and returns an evidence-grounded response[cite: 1].

---

## 2. Detailed Description

The objective is to develop **SatQuery AI**, a software-based agentic vision-language assistant for analysing single and paired remote-sensing images through natural-language queries[cite: 1]. Single-image understanding is a mandatory baseline, while the principal focus is joint reasoning over paired cross-modal and multitemporal imagery[cite: 1].

### Defined Input Scope
* **Single image:** One optical/multispectral or SAR image for captioning, visual question answering, and text-guided region grounding[cite: 1].
* **Cross-modal pair:** Co-registered optical/multispectral and SAR images of the same geographic area for joint information extraction and cross-modal analysis[cite: 1].
* **Bi-temporal pair:** Two spatially corresponding images of the same geographic area acquired at different times for change detection, change description, and change-based visual question answering[cite: 1].
* **Supported formats:** GeoTIFF or TIFF for geospatial imagery[cite: 1]. PNG and JPEG inputs may be accepted only for the prescribed public benchmark datasets[cite: 1].

### Mandatory Functional Scope
* **Remote-sensing adaptation:** At least one visual or vision-language component must be fine-tuned or otherwise adapted using `BigEarthNet.txt` or any open source training data[cite: 1].
* **Single-image baseline:** Visual question answering shall be mandatory[cite: 1]. Each solution must additionally implement either captioning/scene description or text-guided region grounding[cite: 1].
* **Multi-image change analysis:** Change description or change-based visual question answering from a bi-temporal image pair shall be mandatory[cite: 1]. A spatial change map may also be generated where reference masks are available[cite: 1].
* **Cross-modal pair analysis:** The system must extract complementary information from a co-registered optical/multispectral and SAR image pair[cite: 1].
* **Agentic orchestration:** The system must automatically select, sequence, and execute the appropriate specialist models or tools according to the query and input configuration[cite: 1].

### Representative Queries
* *"Describe the land-cover and major objects visible in this image."*[cite: 1]
* *"Highlight the water body referred to in the query."*[cite: 1]
* *"What changed between these two dates, and where did the change occur?"*[cite: 1]
* *"Use the optical and SAR images together to identify built-up and water-covered regions."*[cite: 1]
* *"Has the built-up area increased, decreased, or remained unchanged?"*[cite: 1]

---

## 3. Agentic Model and Tool Orchestration

The system may use multiple specialised components, such as a remote-sensing VQA or captioning model, a grounding model, a change-understanding or change-VQA model, and an optical-SAR fusion or information-extraction model[cite: 1].

The controller is expected to:
* Interpret the query and classify the requested task[cite: 1].
* Check the number, modality, format, metadata, and compatibility of the input images[cite: 1].
* Select one or more models or tools from a predefined registry[cite: 1].
* Configure only permitted task parameters and execute the selected workflow[cite: 1].
* Combine textual and spatial outputs, estimate confidence, and return visual evidence[cite: 1].
* Provide an auditable execution summary containing the selected task, model/tool names, and key parameters[cite: 1].

> **Note on Evaluation:** The controller may perform internal task planning; however, only the observable execution trace, including the selected task, models or tools, permitted parameters, and outputs will be evaluated[cite: 1]. Internal reasoning text is neither required nor evaluated[cite: 1].

---

## 4. Expected Solution & Deliverables

### Expected Solution
An interactive GUI or web application with an agentic remote-sensing AI backend[cite: 1]. It should accept supported image inputs and natural-language queries, select the appropriate specialist workflow, and return evidence-grounded textual and visual results[cite: 1].

The solution must include:
* Input upload and compatibility checking[cite: 1].
* A remote-sensing-adapted vision-language component[cite: 1].
* Specialist tools for VQA, captioning or grounding, change understanding, and optical-SAR analysis[cite: 1].
* An agentic controller for task routing, tool execution, and output integration[cite: 1].
* Visual evidence, confidence information, execution summaries, and downloadable reports[cite: 1].

Each solution must demonstrate single-image VQA, one additional single-image task, multitemporal change understanding, optical-SAR paired-image analysis, and agentic model/tool orchestration[cite: 1]. A generic LLM or VLM without remote-sensing adaptation will not satisfy the requirements[cite: 1].

### Deliverables
* An interactive GUI or web application with an agentic remote-sensing AI backend[cite: 1].
* Codes and models, including test and demonstration pipelines[cite: 1].

### Implementation Scope
The system shall support single optical/multispectral or SAR images, co-registered optical-SAR pairs, and bi-temporal pairs in GeoTIFF/TIFF or approved benchmark formats[cite: 1]. It must perform single-image VQA, one additional single-image task, change analysis, optical-SAR joint analysis, and agentic model/tool selection through an interactive GUI or web application[cite: 1].

---

## 5. Evaluation / Judging Criteria

Final evaluation will use prescribed public benchmark test subsets and an ISRO/SAC evaluation dataset[cite: 1]. Scores will be normalised before combining different metrics[cite: 1].

| Evaluation Component | Metric / Evidence | Weight |
| :--- | :--- | :---: |
| **Agentic task routing and tool orchestration** | Correct task and specialist-model/tool selection, valid execution sequence, input validation, permitted-parameter configuration, and invalid-call rate | **20%**[cite: 1] |
| **Single-image remote-sensing VLM performance** | VRSBench and RSVQA VQA accuracy; VRSBench captioning or grounding metrics, depending on the implemented task | **20%**[cite: 1] |
| **Multitemporal change understanding** | CDVQA average and overall answer accuracy, change-map F1-score and IoU only where reference change masks are provided | **25%**[cite: 1] |
| **ISRO cross-modal paired-image analysis** | Cartosat-2S optical and RISAT SAR pairs: query-answer accuracy, information-extraction F1/IoU, and evidence localisation | **25%**[cite: 1] |
| **Robustness, usability, and reporting** | GeoTIFF/TIFF handling, graceful error messages, latency, confidence reporting, visual evidence, and downloadable report | **10%**[cite: 1] |

Public benchmarks will be evaluated using the prescribed test splits[cite: 1]. The ISRO/SAC evaluation set will contain pre-georeferenced and co-registered Cartosat-2S optical and RISAT SAR image pairs, with task-specific reference answers, labels, bounding boxes, or masks, as applicable[cite: 1]. Evaluation annotations will not be disclosed to participating teams[cite: 1].

---

## 6. Datasets & Resources

### Training / Fine-Tuning Dataset
* **BigEarthNet.txt:** Primary dataset for remote-sensing adaptation using co-registered Sentinel-1 SAR, Sentinel-2 multispectral imagery, and diverse text annotations[cite: 1].  
  Paper / Reference: [https://arxiv.org/abs/2603.29630](https://arxiv.org/abs/2603.29630)[cite: 1]  
  *(All datasets are available online open source.)*[cite: 1]

### Public Evaluation Benchmarks
* **VRSBench:** For remote-sensing image captioning, visual grounding, and VQA[cite: 1].  
  Reference: [https://arxiv.org/abs/2406.12384](https://arxiv.org/abs/2406.12384)[cite: 1]
* **RSVQA:** For single-image remote-sensing visual question answering[cite: 1].  
  Reference: [https://arxiv.org/abs/2003.07333](https://arxiv.org/abs/2003.07333)[cite: 1]
* **CDVQA:** For change-detection-based visual question answering using multitemporal image pairs[cite: 1].  
  Reference: [https://arxiv.org/abs/2112.06343](https://arxiv.org/abs/2112.06343)[cite: 1]

### ISRO/SAC Evaluation Data
* A hidden evaluation set of pre-georeferenced and co-registered Cartosat-2S optical imagery and RISAT SAR imagery will be used for cross-modal paired-image analysis[cite: 1].
* Bi-temporal pairs and corresponding annotations or question-answer references will be provided where required for change-analysis evaluation[cite: 1].
* ISRO datasets will be provided during testing on hackathon day[cite: 1].
