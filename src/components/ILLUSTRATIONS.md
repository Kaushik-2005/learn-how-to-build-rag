# Illustration inventory

The illustrations are stored as reusable Astro components in this directory. They are native HTML/CSS/SVG visuals, not generated image files.

| Chapter | Illustration | Component / mode | Used for |
| --- | --- | --- | --- |
| Homepage | Knowledge illustration | `KnowledgeIllustration.astro` | Unstructured knowledge -> retrieval -> grounded response |
| Chapter 1 | Two kinds of memory | `RagIllustration.astro` with `kind="rag-basics"` | Parametric model memory complemented by selected, traceable external evidence |
| Chapter 2 | Complete pipeline | `PipelineDiagram.astro` | Indexing path and query path |
| Chapter 3 | Source map | `RagIllustration.astro` with `kind="sources"` | PDFs, web, structured data, repositories, collaboration, and media |
| Chapter 3 | Loader contract | `RagIllustration.astro` with `kind="loading-flow"` | Source -> loader -> content and metadata -> document record |
| Chapter 3 | Structure preservation | `RagIllustration.astro` with `kind="extract-structure"` | Table extraction preserving row/header relationships |
| Chapter 4 | Document preparation | `RagIllustration.astro` with `kind="cleaning"` | Decode, clean, validate, and attach provenance |
| Chapter 4 | Preparation record | `RagIllustration.astro` with `kind="prep-flow"` | Raw source -> extracted representation -> prepared representation -> ready for chunking |
| Chapter 5 | Chunk boundaries and overlap | `RagIllustration.astro` with `kind="chunking"` | Meaningful split with repeated boundary context |
| Chapter 5 | Recursive separator priority | `RagIllustration.astro` with `kind="recursive-flow"` | Larger semantic separators before smaller fallback cuts |
| Chapter 5 | Chunking policy | `RagIllustration.astro` with `kind="decision-record"` | Boundaries, limits, overlap, and traceability made explicit |
| Chapter 5 | Context expansion | `RagIllustration.astro` with `kind="context-flow"` | Child chunks -> parent context -> final context |
| Chapter 5 | Pipeline position | `RagIllustration.astro` with `kind="chunk-position"` | Chunking highlighted between preparation and representation |
| Chapter 6 | Embedding space | `RagIllustration.astro` with `kind="embeddings"` | Text represented as vectors |
| Chapter 6 | Embedding flow | `RagIllustration.astro` with `kind="embedding-flow"` | Text/query encoders -> vectors -> candidates |
| Chapter 7 | Vector record | `RagIllustration.astro` with `kind="vector-record"` | Embedding, identity, provenance, metadata, and access constraints |
| Chapter 7 | Exact vs approximate search | `RagIllustration.astro` with `kind="search-modes"` | Exhaustive comparison versus candidate subset exploration |
| Chapter 7 | HNSW layers | `RagIllustration.astro` with `kind="hnsw-layers"` | Sparse upper graph moves and dense lower-layer refinement |
| Chapter 7 | IVF + PQ | `RagIllustration.astro` with `kind="ivf-pq"` | Coarse partition probing and compact product-quantized codes |

When adding a new chapter illustration, add its component usage to this table and keep the visual focused on a mechanism, transformation, or relationship that prose alone does not explain as clearly.
