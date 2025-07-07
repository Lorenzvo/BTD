# 📦 Debian Package Statistics CLI — Canonical Technical Assessment

## 🧾 Overview

This CLI tool fetches and parses the Debian `Contents-ARCH.gz` index file for a given architecture (like `amd64`, `arm64`, etc.) and prints the top 10 packages with the most associated files. It’s written in Go and was built with simplicity, clarity, and clean iteration in mind. Each commit reflects a meaningful change — not just code, but decisions.

---

## 🚀 How to Run

```bash
go run main.go amd64
```

This downloads and parses:

```
http://ftp.uk.debian.org/debian/dists/stable/main/Contents-amd64.gz
```

Example output:

```
bash       1234
coreutils  1123
dpkg       1101
...
```

---

## 🧠 Thought Process

```
I approached this the way I usually do: start with the structure, focus on making things work, and keep things readable and adaptable as I go. I committed early and often to reflect how I think through a problem — get something working, make it better, clean it up.

The core logic is straightforward: read a big file line by line, count how many times each package shows up, and sort the results. I built around that and added practical things like error handling, a test for parsing logic, and a helper script for testing offline.

Performance matters, but I didn't over-optimize — buffer size is tuned, and memory use is reasonable. The whole thing can scale if needed.
```

---

## 🧪 Testing

```bash
go test
```

This runs a test on the line parser to make sure it counts packages correctly.

Optional test file (offline use):

```bash
./scripts/fetch_test_file.sh amd64
```

Saves output to:

```
testdata/sample_contents.gz
```

---

## 🕒 Time Spent

```
About 2.5 hours total:

- Setup and base functionality
- Parser and sorting
- Validation, comments, testing
- Git cleanup and writing this
```

---

## 📁 Project Structure

```
package_statistics/
├── main.go
├── main_test.go
├── go.mod
├── README.md
├── scripts/
│   └── fetch_test_file.sh
├── testdata/
│   └── sample_contents.gz
```

---

## 💡 If I Extended It

```
- Add flags for --top N, --offline
- Cache downloads locally
- Support multiple architectures
- Use goroutines to parse faster
- Wrap it up with better CLI UX
```

---

## 🙋‍♂️ About Me

```
I'm a recent CS grad from UC Berkeley focused on backend and systems work. I care a lot about writing solid, efficient tools that do their job and are easy to build on. I tend to think modularly and care about committing with intention, even on small scripts like this one.
```
