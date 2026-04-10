# bullinger-patristic-detection

Working files for the retrieval of patristic references in Heinrich Bullinger's 16th-century correspondence.
 
- dense retrieval: bi-encoder candidate generation + cross-encoder reranking (using LociSimiles / their fine-tuned Cross-Encoder)
- Biblical pre-filtering via PASSIM to elimate Vulgate citations before retrieval
- Evaluated against a 100-entry validation dataset (50 explicit / 50 implicit references) using Recall@k and MRR
- topic-informed + graph-neighbourhood retrieval experiments

```
data/               chunked VD_BDC and VD_PSC corpora + Vulgate
evaluation/         metric outputs based on retrieval results
figures/            plots
passim/             biblical pre-filtering (PASSIM) metric outputs
scripts/            notebooks for all stages
```

## Scripts

| Notebook | Description |
|----------|-------------|
| `chunking-vulgate.ipynb` | chunks the Vulgate into verse windows for biblical filtering |
| `embeddings-laberta_vulg.ipynb` | Computes LaBERTa embeddings for BDC and PSC chunks |
| `embeddings-sEncoder.ipynb` | Computes sentence-transformer embeddings for BDC and PSC chunks |
| `figures.ipynb` | Generates plots and visualisations for analysis and evaluation |
| `locisimiles.ipynb` | Runs the LociSimiles baseline |
| `retrieval-faiss-graph.ipynb` | Graph-neighbourhood retrieval experiments |
| `retrieval-faiss-top100-rerank.ipynb` | Two-stage cross-encoder retrieval with LaBERTA |
| `retrieval-faiss.ipynb` | Baseline dense retrieval (cosine sim) |
| `retrieval-metrics.ipynb` | Computes Recall@k and MRR against the validation dataset |
| `transform-locisimiles.ipynb` | Transforms LociSimiles output into evaluation-compatible format |
| `vulgate-filtering-BOW-threshold-analysis.ipynb` | BOW threshold analysis for biblical passage filtering |
| `vulgate-filtering-passim-analysis.ipynb` | Analysis of PASSIM biblical filtering results |
| `vulgate-filtering-passim.ipynb` | Runs PASSIM to detect and filter Vulgate passages from BDC letters |

## Related Repos 
- [Bullinger Digital Correspondence (BDC)](https://github.com/stazh/bullinger-korpus-tei) 
- [Patristic Source Corpus (PSC)](https://github.com/len-rtz/bullinger-patristic-psc) 
- [bullinger-patristic-annotations](https://github.com/len-rtz/bullinger-patristic-annotations)
- [LociSimiles](https://github.com/julianschelb/locisimiles)


## Stack

`faiss-cpu` · `sentence-transformers` · `torch` · `lxml` · `pyspark`