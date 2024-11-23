This is an theoretical investigation (and pilot development plan) in the application of deep language models in creating psychotherapist assistant software sparked by my own doctor showing me one that was available to him now. This software recorded our session, displayed a transcript, and when prompted, stopped recording and generated a summary of our session. This summary was mostly correct, but muddled some details, and in one area the summary mistook a speaker. It seemed that this program was doing direct summarizing, maybe fine tuned for psychotherapy session transcripts, and might not even be doing speaker diarisation. I thought assuming that was true, there must be a better way that leverages not only the medium of psychotherapy and applies an intermediate diagnostic layer that points out medically important considerations (recognizing someone is depressed, manic, noting problematic relationships/behaviors, noting medication effectiveness with regard to patient's medical history, etc.) but also attends to token spans of the transcript pertaining to entity-tagged diagnostically important information (symptoms, medications, cognition, emotions, behaviors, social factors), attending to the full patient history, and retrieved entity-tagged articles from a medical corpus. Another attention layer would then filter the text area (and entity tokens) that was relevant for each diagnostic "note" (structured/unstructured). After the medically relevant insights are generated, both the original transcript and medical notes pertaining to areas of the transcript would be used to generate a session summary, recommendations of information to add to patient history which the doctor can either accept or reject, and recommendations of action for the doctor. Of course all of these except the transcripts would be editable by the doctor, and possibly used to improve future accuracy. Although there is a blaring issue in my practical approach, I don't have the approvals, resources, licenses, lawyers, etc., to do data collection or model training at the scale required to develop a good implementation of the proposed model, but what I can do is work on the core transcript analysis, tagging, and information retrieval approach.\
I propose utilizing MentalBERT (trained on a general mental health corpus) to attend to the transcript and patient history and entity tag words/sequences of words that pertain to psychologically relevant information (conditions, medications, behaviors, relationships, etc.), and use non-patient entities to retrieve diagnostically relevant documents. In the future, another language model would sit above this entity-tagged information, with retrieved documents, and produce the sequence of diagnostic notes pertaining to areas of the transcript. Then on top of both the entity-tagged transcript and diagnostic notes (possibly with "cited" relevant passages of documents instead of the entire document [cherry picking?]) a summarization model would produce the final session summary along with another model for proposed additions to patient history and therapist action items. Theoretically these last few tasks could be handled by a modern generative model like GPT-4 (or the 4o and 4o-mini models) through API calls, although fine tuning would be preferred (if I somehow had the data to train it on).

Papers: \
Detecting Depression and Anxiety on Social Media Using Selective Masking ([link](https://repositum.tuwien.at/bitstream/20.500.12708/198293/1/Mullatahiri%20Princ%20-%202024%20-%20Detecting%20Depression%20and%20Anxiety%20on%20))\
Task-Specific Transformer-Based Language Models in Health Care: Scoping Review ([link](https://medinform.jmir.org/2024/1/e49724/PDF))\
BioALBERT: A Simple and Effective Pre-trained Language Model for Biomedical Named Entity Recognition ([link](https://ieeexplore.ieee.org/document/9533884))\
Mental Illness Detection Using NLP ([link](https://scholarworks.calstate.edu/downloads/ms35th72p))\
Detecting Depression and Anxiety on Social Media Using Selective Masking ([link](https://repositum.tuwien.at/bitstream/20.500.12708/198293/1/Mullatahiri%20Princ%20-%202024%20-%20Detecting%20Depression%20and%20Anxiety%20on%20))
