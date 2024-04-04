# github-actions

Projetos com github-actions

## Steps

Criar pasta .github

Criar pasta workflows

Criar arquivo workflow.yaml, no caso abaixo realizando um teste de performance utilizando k6.io:

    name: Continuos Integration

    on: [pull_request, push, issues, issue_comment]
    # on: pull_request

    jobs:
    Continuos-Integration:
        runs-on: ubuntu-latest

        steps:
        - uses: actions/checkout@v3
        - name: teste-k6
        run: |
            sudo gpg -k
            sudo gpg --no-default-keyring --keyring /usr/share/keyrings/k6-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C5AD17C747E3415A3642D57D77C6C491D6AC1D69
            echo "deb [signed-by=/usr/share/keyrings/k6-archive-keyring.gpg] https://dl.k6.io/deb stable main" | sudo tee /etc/apt/sources.list.d/k6.list
            sudo apt-get update
            sudo apt-get install k6
            k6 run k6/script.js
            echo "Teste executado com sucesso!!!"
