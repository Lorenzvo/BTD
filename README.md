## 🧠 My Thought Process

I approached this problem by breaking it into manageable pieces and committing progress in logical stages, as I would in a real engineering workflow.

---

## 🧩 Problem Breakdown

1. **Understand the Contents file format** — Each line maps a file path to one or more space-separated packages.
2. **Fetch and decompress** the appropriate `.gz` file for the requested architecture.
3. **Stream and parse the file** line by line, to avoid memory issues.
4. **Map package → file count**, incrementing counts as packages are encountered.
5. **Sort and display the top 10** packages by number of associated files.

---

## 🔨 Development Stages

I developed and committed the code incrementally:

- Initial CLI structure and URL fetch  
- Gzip decompression and buffered file reading  
- Line parsing and counting logic  
- Sorting logic and top 10 output  
- Input validation and robust error handling  
- Performance improvements via buffer tuning  
- Inline comments and code cleanup  
- Unit test for `processLine()` function  
- Local test script to support offline development  

Each commit reflects a specific, self-contained improvement — not just code, but thought process.

---

## 🧪 Testing

### ✅ Unit Test

Run:

```sh
go test
