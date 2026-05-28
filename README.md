# bullinger-patristic-detection

Working files for the retrieval of patristic references in Heinrich Bullinger's 16th-century correspondence.
 
- dense retrieval: bi-encoder candidate generation + cross-encoder reranking (using LociSimiles / their fine-tuned Cross-Encoder outside of pipeline)
- Biblical pre-filtering via PASSIM to elimate Vulgate citations before retrieval
- Evaluated against a 100-entry validation dataset (50 explicit / 50 implicit references, see [bullinger-patristic-annotations](https://github.com/len-rtz/bullinger-patristic-annotations)
- topic-informed + graph-neighbourhood retrieval experiments

```
data/               chunked VD_BDC and VD_PSC corpora + Vulgate (full corpus for both can be accessed [here](https://github.com/stazh/bullinger-korpus-tei) and [here](https://github.com/len-rtz/patristic-sources))
evaluation/         metric outputs based on retrieval results
figures/            plots
passim/             biblical pre-filtering (passim) metric outputs
scripts/            notebooks for all stages
```

## Scripts

| Notebook | Description |
|----------|-------------|
| `embeddings-laberta_vulg.ipynb` | Computes LaBERTa embeddings for BDC and PSC chunks with mean pooling |
| `embeddings-sEncoder.ipynb` | Computes sentence-transformer embeddings for BDC and PSC chunks |
| `figures.ipynb` | Generates plots and visualisations for analysis and evaluation |
| `graph-rrf-pipeline.ipynb` | Graph-neighbourhood retrieval (RRF) |
| `topic-informed-retrieval.ipynb` | Topic-informed retrieval (RRF) |
| `locisimiles.ipynb` | LociSimiles |
| `passim-baseline-retrieval.ipynb` | string alignment using passim + GT evaluation | 
| `retrieval-faiss-top100-rerank.ipynb` | Two-stage cross-encoder retrieval outside Locisimiles (FAISS) |
| `retrieval-faiss.ipynb` | Baseline dense retrieval (cosine sim) |
| `retrieval-metrics.ipynb` | Computes Recall@k and MRR against the ground truth dataset |
| `transform-locisimiles.ipynb` | Transforms LociSimiles output into evaluation-compatible format |
| `vulgate-filtering-passim-analysis.ipynb` | Analysis of PASSIM biblical filtering results |
| `vulgate-filtering-passim.ipynb` | Runs PASSIM to detect and filter Vulgate passages from BDC letters |

## Related Repos 
- [Bullinger Digital Correspondence (BDC)](https://github.com/stazh/bullinger-korpus-tei) 
- [Patristic Source Corpus (PSC)](https://github.com/len-rtz/bullinger-patristic-psc) 
- [bullinger-patristic-annotations](https://github.com/len-rtz/bullinger-patristic-annotations)
- [LociSimiles](https://github.com/julianschelb/locisimiles)
- [itserr Latin Models](https://huggingface.co/collections/itserr/wp8-latin-embeddings)