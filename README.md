# Awesome Clinical AI for Pharmacy & Surgery [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of datasets, tools, models, and reading for building AI at the intersection of **medication safety, surgical care, and underserved-population access.**

Most "awesome AI in healthcare" lists are broad. This one is deliberately narrow. It is maintained by a BA/MD student focused on interventional cardiology, cardiothoracic/vascular surgery, and bringing surgical and pharmacy care to rural and underserved communities — so the curation leans toward resources that are actually usable for building tools in those areas, not just publishing about them.

If a resource isn't openly accessible, or is purely a closed commercial product with no research or developer entry point, it generally isn't here.

## Contents

- [Datasets](#datasets)
  - [Critical Care & EHR](#critical-care--ehr)
  - [Medication & Pharmacology](#medication--pharmacology)
  - [Surgical & Endoscopic Video](#surgical--endoscopic-video)
  - [Medical Imaging](#medical-imaging)
- [Tools & Libraries](#tools--libraries)
  - [Clinical NLP](#clinical-nlp)
  - [Medication & Interaction Tooling](#medication--interaction-tooling)
  - [Common Data Models & Interoperability](#common-data-models--interoperability)
- [Models](#models)
- [Benchmarks & Challenges](#benchmarks--challenges)
- [Reading](#reading)
  - [Medication Safety & Pharmacovigilance](#medication-safety--pharmacovigilance)
  - [Surgical AI](#surgical-ai)
  - [Equity & Access](#equity--access)
- [Learning Resources](#learning-resources)
- [Related Lists](#related-lists)
- [Contributing](#contributing)

---

## Datasets

### Critical Care & EHR

- [MIMIC-IV](https://physionet.org/content/mimiciv/) — De-identified ICU and hospital records from Beth Israel Deaconess Medical Center, including labs, prescriptions, procedures, and notes. The single most widely used open critical-care dataset; requires a free credentialed PhysioNet account and a data-use agreement.
- [MIMIC-III](https://physionet.org/content/mimiciii/) — The prior generation, still heavily used and well-documented; good starting point because so many tutorials target it.
- [eICU Collaborative Research Database](https://physionet.org/content/eicu-crd/) — Multi-center ICU data across many US hospitals, useful for studying generalization across sites — directly relevant to rural vs. academic-center differences.
- [PhysioNet](https://physionet.org/) — The umbrella repository hosting the above plus hundreds of physiologic-signal and clinical datasets (ECG, waveforms, etc.), several relevant to cardiology.

### Medication & Pharmacology

- [RxNorm](https://www.nlm.nih.gov/research/umls/rxnorm/) — NLM's normalized naming system for clinical drugs; the backbone for mapping brand/generic names and linking to interaction data. Free API.
- [DrugBank (Open Data)](https://go.drugbank.com/releases/latest) — Structured drug, target, and interaction data; an open academic subset is available alongside the commercial full release.
- [SIDER](http://sideeffects.embl.de/) — Database of marketed-drug side effects extracted from labels; useful for adverse-event modeling.
- [FDA openFDA](https://open.fda.gov/) — Public APIs over FAERS adverse-event reports, drug labels, and recalls; the practical entry point for pharmacovigilance projects.
- [FAERS](https://www.fda.gov/drugs/surveillance/questions-and-answers-fdas-adverse-event-reporting-system-faers) — The FDA Adverse Event Reporting System; raw quarterly files behind openFDA.

### Surgical & Endoscopic Video

- [CholecT50 / Cholec80](https://camma.unistra.fr/datasets/) — Laparoscopic cholecystectomy videos annotated for surgical phases and action triplets (instrument-verb-target); a standard benchmark for surgical activity recognition.
- [EndoVis (MICCAI Endoscopic Vision Challenges)](https://endovis.grand-challenge.org/) — A recurring family of challenges covering instrument segmentation, workflow recognition, and more.
- [Cataract-101](http://ftp.itec.aau.at/datasets/ovid/cat-101/) — 101 annotated cataract-surgery videos for phase recognition.
- [JIGSAWS](https://cirl.lcsr.jhu.edu/research/hmm/datasets/jigsaws_release/) — Robotic surgical gesture and skill-assessment dataset (suturing, knot-tying, needle-passing) with kinematic data — relevant to surgical-skill AI.

### Medical Imaging

- [MedMNIST](https://medmnist.com/) — A lightweight, standardized collection of biomedical image classification datasets; excellent for prototyping and teaching before scaling to full-resolution data.
- [CheXpert](https://stanfordmlgroup.github.io/competitions/chexpert/) — Large chest X-ray dataset with uncertainty labels.
- [The Cancer Imaging Archive (TCIA)](https://www.cancerimagingarchive.net/) — Large public archive of de-identified cancer imaging across modalities and sites.

## Tools & Libraries

### Clinical NLP

- [scispaCy](https://allenai.org/data/scispacy) — spaCy pipelines for biomedical and clinical text, with entity linking to UMLS.
- [medspaCy](https://github.com/medspacy/medspacy) — Clinical NLP toolkit built on spaCy, including context detection (negation, historical, hypothetical) — critical for not misreading "no chest pain" as "chest pain."
- [cTAKES](https://ctakes.apache.org/) — Apache's long-standing clinical text extraction system.
- [Stanza (biomedical models)](https://stanfordnlp.github.io/stanza/biomed.html) — Stanford's neural NLP with biomedical and clinical model packages.

### Medication & Interaction Tooling

- [RxNav / RxNorm API](https://lhncbc.nlm.nih.gov/RxNav/) — NLM's web services for drug normalization, interaction lookup, and RxClass drug classes; the free foundation for medication tooling.
- [RxSentinel](https://github.com/baeseongsu) — *(placeholder — replace with your own RxSentinel repo link once it's up)* A transparent, formulary-backed interaction screener and PTCB study engine.
- [PharmPy](https://pharmpy.github.io/) — Library for pharmacometric model handling and workflows.

### Common Data Models & Interoperability

- [OHDSI / OMOP CDM](https://www.ohdsi.org/data-standardization/) — The Common Data Model that lets analyses run across institutions' data — a key enabler of multi-site (including rural-network) research.
- [HL7 FHIR](https://www.hl7.org/fhir/) — The modern interoperability standard for exchanging health data; most EHR integrations speak it.
- [Synthea](https://synthetichealth.github.io/synthea/) — Generates realistic synthetic patient records with no privacy constraints — ideal for prototyping and teaching when you can't touch real PHI.

## Models

- [Bio_ClinicalBERT](https://huggingface.co/emilyalsentzer/Bio_ClinicalBERT) — BERT pretrained on MIMIC clinical notes; a common starting point for clinical text tasks.
- [BioBERT](https://github.com/dmis-lab/biobert) — BERT pretrained on biomedical literature (PubMed/PMC).
- [PubMedBERT](https://huggingface.co/microsoft/BiomedNLP-BiomedBERT-base-uncased-abstract-fulltext) — Pretrained from scratch on biomedical text, often stronger than continued-pretraining approaches on biomedical NLP.
- [GatorTron](https://huggingface.co/UFNLP/gatortron-base) — Large clinical language model trained on a very large corpus of clinical notes.

## Benchmarks & Challenges

- [n2c2 / i2b2 NLP Challenges](https://portal.dbmi.hms.harvard.edu/) — Long-running shared tasks on clinical NLP (de-identification, medication extraction, relations) with released annotated data.
- [MedQA (USMLE)](https://github.com/jind11/MedQA) — Medical question-answering benchmark drawn from board-style exam questions.
- [Grand Challenge](https://grand-challenge.org/) — A hub for biomedical imaging challenges, including many surgical and radiology tasks.

## Reading

Foundational and orienting reads. Descriptions are summaries in my own words; follow the links for the sources.

### Medication Safety & Pharmacovigilance

- *The Checklist Manifesto* — Atul Gawande. On how simple, well-designed checklists reduce error in complex, high-stakes settings like surgery and prescribing.
- WHO reports on medication safety and adverse drug events — practical framing for why interaction screening and reconciliation matter at the population level.

### Surgical AI

- Reviews of surgical data science and computer-assisted surgery — surveys that map the field from workflow recognition to skill assessment and autonomy levels. Search "surgical data science" for current review articles.
- Literature on surgical phase recognition using the Cholec80/CholecT50 datasets above — a good concrete on-ramp into the methods.

### Equity & Access

- Work on the rural surgical workforce shortage and access gaps — motivates why tools that extend specialist reach (tele-mentoring, decision support) matter.
- Research on algorithmic bias in clinical models, including how models trained at academic centers can underperform elsewhere — essential context before deploying anything in underserved settings.

## Learning Resources

- [MIT Critical Data / "Secondary Analysis of Electronic Health Records"](https://link.springer.com/book/10.1007/978-3-319-43742-2) — Open-access book built around MIMIC; a practical path from raw EHR to analysis.
- [fast.ai](https://www.fast.ai/) — Practical deep learning, a common starting point before specializing into medical imaging.
- [OHDSI "Book of OHDSI"](https://ohdsi.github.io/TheBookOfOhdsi/) — Free, thorough guide to observational health-data research and the OMOP model.

## Related Lists

- [awesome-machine-learning-for-healthcare](https://github.com/baeseongsu/awesome-machine-learning-for-healthcare) by Seongsu Bae — a broader ML-in-healthcare list; a good general complement to this narrower one.
- [awesome-healthcare](https://github.com/kakoni/awesome-healthcare) — Open-source healthcare software and resources.

## Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). In short: one resource per pull request, keep the description to a sentence or two written in your own words, say *why* it's useful (not just what it is), and prefer openly accessible resources. This list values curation over completeness.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE)

To the extent possible under law, the maintainer has waived all copyright and related rights to this curated list itself (CC0). Linked resources remain under their own licenses.
