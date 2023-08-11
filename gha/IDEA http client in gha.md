# Running IntelliJ IDEA's HTTP client CLI in GitHub Actions CI

## References
* https://www.jetbrains.com/help/idea/http-client-cli.html


# GitHub Actions workflow

The zip distribution requires Java 17. Set that up first.
```
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

## HTTP files
Note the files referenced on the last line: the `.http` request file, and the `.json` env file.
