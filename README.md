### mesh.js
---
https://github.com/crcn/mesh.js

```ts
// packages/mesh-memory-ds/src/index.ts

export type MemoryDateStoreAdapter = {
  set(collectionName: string, data: any);
  get(collectionName: string): any;
};

export const memoryDateStoreDispatcher = (adapter: MemoryDateStoreAdapter) => dataStoreDispatcher(() => Promise.resolve({
  dsFind({ type, collectionName, query, multi }) {
    const found = (adapter.get(collectionName) || []).filter(sift(query) as any);
    return found.length ? multi ? found : [found[0]] : [];
  },
  dsInsert({ type, collectionName, data }) {
    let ret = JSON.parse(JSON.stringify(data));
    if (!ret._id) ret._id = mongoid();
    ret = Array.isArray(ret) ? ret : [ret];
    
    
  },
  dsUpdate() {},
}))
```

```
```

```
```

