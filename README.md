# 🧩 Multi-Platform Matrix Build with Artifacts (d7a7edf)

This repository demonstrates a **GitHub Actions matrix build** workflow that builds and uploads artifacts for multiple Node.js versions in parallel.

---

## 🚀 Workflow Overview

**Workflow File:** `.github/workflows/matrix-build.yml`

### Key Features

- **Matrix Strategy:** Runs the build on Node.js versions **14, 16, and 18**  
- **Parallel Jobs:** Each version builds in a separate job simultaneously  
- **Artifact Upload:** Each job generates and uploads a unique artifact  
  - Artifacts are named:  
    - `build-d7a7edf-v14`  
    - `build-d7a7edf-v16`  
    - `build-d7a7edf-v18`  
- **Identifier Step:** Includes the step `matrix-d7a7edf` for validation  
- **Artifacts contain content:** Each file includes build output and metadata text

---

## 🧱 Example Workflow Snippet

```yaml
strategy:
  matrix:
    node-version: [14, 16, 18]

steps:
  - name: matrix-d7a7edf
    run: echo "Building for Node version ${{ matrix.node-version }}"

  - name: Generate build artifact
    run: echo "Build output for version ${{ matrix.node-version }}" > output.txt

  - name: Upload artifact
    uses: actions/upload-artifact@v4
    with:
      name: build-d7a7edf-v${{ matrix.node-version }}
      path: output.txt
