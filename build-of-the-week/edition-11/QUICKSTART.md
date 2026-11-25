# Build of the Week — Edition 11: Build a Tiny RAG Over Your Own Notes

Goal: see retrieval quality with your own eyes. You index 10–20 of your own text
files, ask questions, and read the chunks the retriever returns — with file
names as citations — before any model writes an answer. Retrieval only: no
model key, no cloud, nothing leaves your machine. Budget: under one hour.

## What you need

- Python 3.10 or later
- `pip install scikit-learn` (one package; everything else is the standard library)
- A folder of your own `.txt` or `.md` files (meeting notes, policies, specs)

## Steps

1. Put your files in a folder named `docs/` next to the script below.
2. Save this script as `mini_rag.py`:

```python
import pathlib, re
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity

docs_dir = pathlib.Path("docs")
chunks, sources = [], []
for path in sorted(docs_dir.rglob("*")):
    if path.suffix.lower() not in {".txt", ".md"} or not path.is_file():
        continue
    text = path.read_text(encoding="utf-8", errors="ignore")
    for para in re.split(r"\n\s*\n", text):
        para = para.strip()
        if len(para) >= 80:            # skip stubs and headings-only lines
            chunks.append(para)
            sources.append(path.name)

print(f"Indexed {len(chunks)} chunks from {len(set(sources))} files")
vectorizer = TfidfVectorizer(stop_words="english")
matrix = vectorizer.fit_transform(chunks)

while True:
    q = input("\nQuestion (blank to quit): ").strip()
    if not q:
        break
    scores = cosine_similarity(vectorizer.transform([q]), matrix)[0]
    for i in scores.argsort()[::-1][:3]:
        print(f"\n--- {sources[i]} (score {scores[i]:.2f}) ---")
        print(chunks[i][:600])
```

3. Run it: `python mini_rag.py`
4. Ask five questions you can check by hand against the files. For each one,
   read the three printed chunks first. Note: did the right chunk come back?
   Did a wrong chunk rank above it?
5. Fix one failure by hand: split a long file into smaller pieces, or rename a
   file so its name carries the topic words, then run again and compare.

## What you learn

- The retriever decides what the model can say. A missing or wrong chunk means
  a wrong answer, however strong the model is.
- Chunk size is a trade: too large and the match blurs; too small and the
  context breaks.
- File names in the output are your citations. Any RAG you buy should show
  them the same way.

## Next step

Swap TF-IDF for embeddings later if you need meaning-based matching. The
shape stays the same: index → retrieve → read the chunks → answer from them.
That shape is RAG, as Edition 11's explainer lays out
(survey source: https://arxiv.org/abs/2611.30181).
