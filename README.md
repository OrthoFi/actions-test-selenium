# Selenium as a GitHub Action for OrthoFi!
This runs the OrthoFi Selenium pipeline by tag. You cannot use this to run the entire suite of tests at present - use something like `gh run workflow build.yml --R OrthoFi/tests-selenium` for that. The intended use case here is to make a small scope of integration-type Selenium tests a part of a build pipeline, perhaps conditional to deploy.

To implement this in a GHA script for an upstream project, use code like this:

```
selenium:
  name: Selenium
  needs: [dependencies, lint, test]
  runs-on: windows-latest
  steps:
    - name: Run Selenium tests
      id: selenium
      uses: orthofi/actions-test-selenium@v1
      with:
        browser: <<BROWSER NAME HERE>>
        tag: <<TAG NAME HERE>>
        github-build-token: ${{ secrets.BUILD_GITHUB_TOKEN }}
```
