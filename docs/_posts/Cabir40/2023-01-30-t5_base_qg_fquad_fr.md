---
layout: model
title: French T5ForConditionalGeneration Base Cased model (from JDBN)
author: John Snow Labs
name: t5_base_qg_fquad
date: 2023-01-30
tags: [fr, open_source, t5, tensorflow]
task: Text Generation
language: fr
edition: Spark NLP 4.3.0
spark_version: 3.0
supported: true
engine: tensorflow
annotator: T5Transformer
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained T5ForConditionalGeneration model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `t5-base-fr-qg-fquad` is a French model originally trained by `JDBN`.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/t5_base_qg_fquad_fr_4.3.0_3.0_1675109420285.zip){:.button.button-orange}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/t5_base_qg_fquad_fr_4.3.0_3.0_1675109420285.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
documentAssembler = DocumentAssembler() \
    .setInputCols("text") \
    .setOutputCols("document")

t5 = T5Transformer.pretrained("t5_base_qg_fquad","fr") \
    .setInputCols("document") \
    .setOutputCol("answers")
    
pipeline = Pipeline(stages=[documentAssembler, t5])

data = spark.createDataFrame([["PUT YOUR STRING HERE"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler() 
      .setInputCols("text")
      .setOutputCols("document")
       
val t5 = T5Transformer.pretrained("t5_base_qg_fquad","fr") 
    .setInputCols("document")
    .setOutputCol("answers")
   
val pipeline = new Pipeline().setStages(Array(documentAssembler, t5))

val data = Seq("PUT YOUR STRING HERE").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|t5_base_qg_fquad|
|Compatibility:|Spark NLP 4.3.0+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[documents]|
|Output Labels:|[t5]|
|Language:|fr|
|Size:|923.2 MB|

## References

- https://huggingface.co/JDBN/t5-base-fr-qg-fquad
- https://github.com/patil-suraj/question_generation