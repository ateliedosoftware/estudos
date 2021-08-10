# Problemas e Soluções de Conflitos no Git
Alguns desafios que vamos encontrando no decorrer do aprendizado da ferramenta de versionamento de códigos Git.

## Adicionar e remover submódulos 
Incluir submódulos como parte de seu desenvolvimento Git permite que você inclua outros projetos em sua base de código, mantendo seu histórico separado, mas sincronizado com o seu. É uma maneira conveniente de resolver os problemas de dependência e biblioteca do fornecedor.

## E se precisar remover um submódulo?
Numa situação em que precisei remover um submódulo anteriormente incluído tive um pouco de dificuldade. Abaixo seguem os passos para resolução desse desafio.

### 1º passo - remover a referência (cache) mantendo os arquivos
```shell
git rm --cached submodule_path
```
### 2º passo - remover as entradas ou se for único, o arquivo contendo as referências
```shell
git rm .gitmodules
```
### 3º passo - remove a pasta dentro do submódulo
```shell
rm -rf submodule_path/.git
```
### 4º passo - adiciona a referência e commita o submódulo
```shell
git add submodule_path git commit -m "remove submodule"
```

Com isso o repositório está pronto para contribuições, contendo os arquivos dos submódulos.