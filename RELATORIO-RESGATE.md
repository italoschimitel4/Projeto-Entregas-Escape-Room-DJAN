# Relatório de Resgate - Git Escape Room
**Projeto Entregas em Java**
**Instituição:** SENAI FATESG
**Equipe:** Ítalo Schimitel, Vitor Hugo Pereira e Maria Eduarda

## 1. Diagnóstico Inicial
Recebemos um repositório comprometido, com falhas de compilação, lógica quebrada e credenciais vazadas. Através da análise da árvore de commits, identificamos os seguintes pontos de atenção cruciais:
* O commit que apagou o `Validador.java`.
* A branch isolada com a documentação do README.
* A tag `commit-perigoso` indicando vazamento de dados na `release-dev`.

## 2. Evidências Técnicas de Recuperação
* **Erro de Compilação:** O comando `git diff` identificou a remoção do endereço; o problema foi corrigido ajustando a chamada para `repository.salvar()`.
* **Arquivo Perdido:** Os comandos `git log --diff-filter=D` e `git checkout` restauraram a classe `Validador`.
* **Correção do Login:** Houve a restauração dos operadores lógicos (`&&`) e de string (`.equals`) no `LoginService`.
* **Auditoria de Segurança:** O arquivo `application.properties` foi removido da branch e adicionado ao `.gitignore`.

## 3. Conclusão e Aprendizado
* **O histórico é imutável:** Apagar o arquivo sensível da versão atual não eliminou o segredo do histórico; o commit antigo ainda expõe a senha.
* **Rastreabilidade e Auditoria:** Cada linha de código alterada tem um autor e um hash, permitindo isolar e reverter regressões rapidamente.
* **Redução de Riscos:** O Git não é apenas backup, mas uma ferramenta vital de controle de configuração para recuperar projetos após alterações incorretas.