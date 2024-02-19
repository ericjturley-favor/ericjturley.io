# IDEA's HTTP CLI in GHA CI

## Running IntelliJ IDEA's HTTP client CLI in GitHub Actions CI

IDEA has an [HTTP client](https://github.com/favordelivery/intellij-idea-tips/blob/main/http-client/http-client.md).  
The client can make assertions (tests).  
That client can also be run via a CLI.  
So we can put it in a CI build, then.

## GitHub Actions workflow

The zip distribution requires Java 17. Set that up first.
```yaml
    - name: Set up Java
      uses: actions/setup-java@v3
      with:
        distribution: 'temurin'
        java-version: '17'

    - name: Run Http Tests with the Jetbrains HTTP Client CLI
      run: |
        curl -f -L -o ijhttp.zip "https://jb.gg/ijhttp/latest"
        unzip ijhttp.zip
        ./ijhttp/ijhttp http-client/http-tests.http --report --env-file http-client/http-client.env.json --env local
```
[Example `http-tests.yaml` here](https://github.com/favordelivery/recommendations/blob/8cf22a9a5d80c17e5254c5ad4a6c6753b9aa380d/.github/workflows/http-tests.yaml).  
(NOTE: The SONAR-related secrets are not necessary)


### HTTP files
> Note the files referenced on the last line: the `.http` request file, and the `.json` env file.
{style=note}

## Reference commit
[Reference commit](https://github.com/favordelivery/recommendations/commit/8cf22a9a5d80c17e5254c5ad4a6c6753b9aa380d).  
(NOTE: The SONAR-related secrets are not necessary)

### References
<seealso>
    <category ref="other">
        <a href="https://github.com/favordelivery/intellij-idea-tips/blob/main/http-client/http-client.md">IDEA's HTTP client tips</a>
        <a href="https://www.jetbrains.com/help/idea/http-client-cli.html">IDEA's HTTP client CLI docs</a>
    </category>
</seealso>
