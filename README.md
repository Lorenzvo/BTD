# Debian Package Statistics CLI — Canonical Technical Assessment

## Overview

This CLI tool fetches and parses the Debian `Contents-ARCH.gz` index file for a given architecture (like `amd64`, `arm64`, etc.) and prints the top 10 packages with the most associated files. It’s written in Go and was built with simplicity and clean iteration in mind.

---

## How to Run

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

##  Thought Process

```
I approached this the way I usually do: start by understanding the goal, break it into smaller, logical parts, and then solve those pieces one by one. I prefer having something working early, even if it's basic, then iterating and improving. I committed often to reflect those phases of initial structure, functionality, cleanup, and polish.

For this problem, I started by making sure I fully understood the Contents file format and the structure of Debian mirrors. Once I knew what kind of data I was working with, I focused on getting the CLI working and reading it efficiently.

I handled parsing line by line to avoid unnecessary memory usage, then built a map of package counts. After that, I worked on sorting and formatting the output. Only after the full logic was working did I go back to tune performance, add tests, rename variables for clarity, and clean up the code.

Performance matters, but I didn’t over-optimize. The buffer size is tuned, and memory usage is controlled. The whole thing is scalable and can be improved further if needed.

```

---

## Testing

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

## Time Spent

```
About 2.5 hours total:

~30 min setting up the CLI structure, Go module, and architecture validation

~40 min implementing the file download, decompression, and buffered line reading

~30 min parsing logic, counting packages, and sorting results

~20 min adding error handling, input checks, and edge case handling

~20 min writing a unit test for the parsing function and scripting local test support

~30 min final cleanup: renaming variables, writing comments, rewriting commit history, and preparing this README

```

---

## Project Structure

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

## Potential Improvements

```
- Add flags for --top N, --offline
- Cache downloads locally
- Support multiple architectures
- Use goroutines to parse faster
- Wrap it up with better CLI UX

```

---

## About Me

```
I'm a recent CS grad from UC Berkeley focused on backend and systems work. I care a lot about writing solid, efficient tools that do their job and are easy to build on. I tend to think modularly and care about committing with intention, even on small scripts like this one.

```
