# cs-coders-cicd-openshift

Exemplo de criação de uma infraestrutura de CI/CD no Openshift

> Referência ao projeto original do exemplo CI/CD fornecido pela RedHat
> https://github.com/OpenShiftDemos/openshift-cd-demo

## Requisitos

* Openshift Origin ou Minishift (Versão 3.9 ou superior)
* Openshift CLI (Para execução dos comandos no cluster)

## O que será criado ?

* Jenkins 2
* Nexus 3
* SonarQube 6.7

## Executando

* Criando os projetos

```
oc new-project coders-dev --display-name="Coders - Dev"
oc new-project coders-stage --display-name="Coders - Stage"
oc new-project coders-cicd --display-name="Coders - CI/CD"
```

* Concedendo permissão ao Jenkins aos projetos

```
oc policy add-role-to-user edit system:serviceaccount:coders-cicd:jenkins -n coders-dev
oc policy add-role-to-user edit system:serviceaccount:coders-cicd:jenkins -n coders-stage
```

* Executando o template com os Apps

```
oc new-app -n coders-cicd -f cicd-template.yaml
```