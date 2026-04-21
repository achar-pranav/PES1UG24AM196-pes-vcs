# Phase 1: Object Storage Foundation

## Screenshot 1A: Test Results
Run the following command to verify the object store implementation:
```bash
make test_objects && ./test_objects
```
*Save the output as `screenshots/1a.png`.*

## Screenshot 1B: Sharded Directory Structure
Run the following command to show the sharded folder structure in `.pes/objects`:
```bash
find .pes/objects -type f
```
*Save the output as `screenshots/1b.png`.*

---
# Phase 2: Tree Objects

## Screenshot 2A: Test Results
Run the following command to verify the tree implementation:
```bash
make test_tree && ./test_tree
```
*Save the output as `screenshots/2a.png`.*

## Screenshot 2B: Raw Tree Object Inspection
Run the following command to inspect a raw tree object (pick one from the list):
```bash
# First find a tree object hash
find .pes/objects -type f | xargs -n 1 ls -t | head -n 1
# Then use xxd to see its binary content (replace XX/YYYY with actual path)
# xxd .pes/objects/XX/YYYY... | head -20
```
*Save the `xxd` output as `screenshots/2b.png`.*

---
# Phase 3: The Index (Staging Area)

## Screenshot 3A: Staging Workflow
Run the following sequence to test the index implementation:
```bash
make pes
./pes init
echo "Hello PES" > hello.txt
echo "VCS from scratch" > note.txt
./pes add hello.txt note.txt
./pes status
```
*Save the output as `screenshots/3a.png`.*

## Screenshot 3B: Index File Content
Inspect the human-readable index file:
```bash
cat .pes/index
```
*Save the output as `screenshots/3b.png`.*

---
# Phase 4: Commits and History

## Screenshot 4A: Commit History
Run the following sequence to create commits and view the log:
```bash
# Initialize and add files
make pes
rm -rf .pes
./pes init
echo "Initial Content" > hello.txt
./pes add hello.txt
./pes commit -m "Initial commit"

# Modify and commit
echo "Update 1" >> hello.txt
./pes add hello.txt
./pes commit -m "Second commit"

# Add new file and commit
echo "New File" > bye.txt
./pes add bye.txt
./pes commit -m "Third commit"

# View log
./pes log
```
*Save the `pes log` output as `screenshots/4a.png`.*

## Screenshot 4B: Object Store Growth
Check the number of objects created after multiple commits:
```bash
find .pes/objects -type f | sort
```
*Save the output as `screenshots/4b.png`.*

## Screenshot 4C: Reference Chain
Verify how HEAD and branches point to commits:
```bash
cat .pes/HEAD
cat .pes/refs/heads/main
```
*Save the output as `screenshots/4c.png`.*

---
*Completed Implementation of `commit_create` in `commit.c`.*
