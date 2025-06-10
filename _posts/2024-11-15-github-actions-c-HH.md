---
title: Github Actions on C and Python
description: Creating a Github Actions on C and Python
date: 2024-11-15 10:20:00 -0530
categories: [Hobbyist Haven]
tags: [python,c,github,cicd]
image:
  path: /assets/img/blog/2024/c-action/gitcat.png
  lqip: /assets/img/blog/2024/c-action/gitcat.png
---

In my latest GitHub journey, I’ve set up two distinct CI/CD pipelines to streamline the testing process for C and Python projects. By automating both compilation and testing, I can catch issues early, ensure consistent builds, and maintain code quality—right from GitHub! Here’s a breakdown of what I’ve built, the steps involved, and why these workflows make development more efficient.


### Automating C Code Testing with GitHub Actions

I started by creating a GitHub Action workflow for my C calculator application. This workflow leverages Ubuntu as the base environment and is triggered on any push or pull request targeting the `main` branch. Here's how it works:


1. **Installing GCC**: I need to checkout this repo in the environment, that happens in first step. A key step for C projects, this ensures that the calculator app can be compiled consistently across environments.

   

2. **Compiling the C Code**: Using GCC, we compile the app to ensure it builds without issues. This also lets us detect any compiler-related errors early.


3. **Running Tests via Shell Script**: With the app built, I run a shell script that executes a series of tests to verify the calculator’s functionality. Since we cant run shell script directly, I need to make it executable before running.


#### Pipeline Code:
```yaml
name: Calculator Tests by @Balaji303

on: 
  push:
    branches:
      - main

  pull_request:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest

    steps:

      - name: Checkout repository
        uses: actions/checkout@v3


      - name: Install GCC
        run: sudo apt-get install gcc -y


      - name: Compile Calculator App
        run: gcc app/calculator.c -o EXE_calculator


      - name: Make calculator_test_file.sh executable
        run: chmod +x ./calculator_test_file.sh


      - name: Run Tests
        run: ./calculator_test_file.sh
```

### Python CI/CD Workflow with Pytest and Code Coverage

For Python projects, I wanted a more feature-rich workflow. This workflow not only runs tests using `pytest` but also uploads a detailed code coverage report. Here’s the process:


1. **Setting Up Python**: GitHub Actions automatically sets up Python (3.x) on the runner.

   

2.**Installing Dependencies**: All required packages, including `pytest` and `pytest-cov`, are installed using `pip`.


3. **Running Tests and Generating Reports**: `pytest` is used to run unit tests, with results saved in an HTML report. Then these reports are uploaded to the pipeline artifact.


4. **Uploading Code Coverage to Codecov**: The final step uploads the coverage results to Codecov, where I can review code coverage insights.


#### Pipeline Code:

```yaml
name: Calculator Tests by @balaji303


on: 
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest

    steps:

      - name: Checkout repository
        uses: actions/checkout@v4
        with:
          fetch-depth: 0
        
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.x'

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt
          pip install pytest pytest-cov        

      - name: Run tests and generate HTML report
        run: |
          pytest --html=report.html app/test_calculator.py

      - name: Upload HTML report
        uses: actions/upload-artifact@v4
        with:
          name: test-report
          path: |
            report.html
            assets/

      - name: Run tests
        run: |
          pytest --cov --cov-report=xml

      - name: Upload results to Codecov
        uses: codecov/codecov-action@v4
        with:
          token: ${{ secrets.CODECOV_TOKEN }}
```

#### Key Takeaways

- **Consistency in Builds**: Automating the compilation ensures that the application builds correctly every time.

- **Testing Across Environments**: Testing in a controlled CI/CD environment catches potential issues that may not show up locally.

- **Comprehensive Coverage**: With code coverage reporting, I can easily see how much of my code is tested, highlighting areas for improvement.


Setting up these pipelines was both challenging and incredibly rewarding, and I’m excited to share these insights with the community. If you're interested in exploring my GitHub Actions workflows, check out the links below:

- Github actions for C [^1-repo] 

- Github actions for Python [^2-repo] 

Automating CI/CD with GitHub Actions has truly transformed my workflow. I look forward to more enhancements and sharing my journey with you all!

[^1-repo]: [C GitHub Action](https://github.com/MadeByBalaji/c-calculator/actions)
[^2-repo]: [Python GitHub Action](https://github.com/MadeByBalaji/py-calculator/actions)