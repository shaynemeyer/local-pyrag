# Testing Vector

```bash
python -i
from pyrag.config import load_config
from pyrag.stores import make_store, StoredChunk
store = make_store(load_config())
store.upsert_document("demo.txt", "h1", [StoredChunk(0, "The quick brown fox", [0,0]*768, {})])
```
