.github/workflows/build.yml
name: Build APK

on:
  push:
    branches: [ main ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Create test file
        run: echo "Workflow is working!" > test.txt
      
      - name: Upload file
        uses: actions/upload-artifact@v4
        with:
          name: test-file
          path: test.txt