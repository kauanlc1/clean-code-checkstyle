# Clean Code - Linters (Java & Checkstyle)

## ✨ Tabela de Conteúdos

- [Clean Code - Linters](#clean-code---linters-java--checkstyle)
- [Sobre o Linter](#sobre-o-linter)
- [Instalação e Configuração](#instalação-e-configuração)
  - [Pré-Requisitos](#pré-requisitos)
  - [Configuração Inicial no IntelliJ IDEA](#configuração-inicial-no-intellij-idea)
- [Verificação de Código com Checkstyle](#verificação-de-código-com-checkstyle)
- [Configuração das Regras de Estilo](#configuração-das-regras-de-estilo)
- [💻 Exemplo de Código a Ser Estilizado](#-exemplo-de-código-a-ser-estilizado)
- [📜 Relatório de Erros do Checkstyle](#-relatório-de-erros-do-checkstyle)
- [🔧 Regras de Estilo Comuns](#-regras-de-estilo-comuns)
- [Suprimindo Regras do Checkstyle com `@SuppressWarnings("checkstyle")`](#-suprimindo-regras-do-checkstyle-com-suppresswarningscheckstyle)
- [📜 Conclusão](#-conclusão)
## Sobre o Linter

**Checkstyle** é uma ferramenta de análise estática para código Java que verifica se o código está em conformidade com convenções de estilo de codificação predefinidas. Ele é amplamente usado para garantir que o código seja limpo, padronizado, legível e de fácil manutenção.

## Instalação e Configuração

### Pré-Requisitos

Antes de instalar e usar o Checkstyle, verifique se você possui os seguintes pré-requisitos:

- JDK 8 ou superior instalado
- IntelliJ IDEA instalado

### Configuração Inicial no IntelliJ IDEA

1. Abra seu projeto no IntelliJ IDEA.
2. Acesse `File` > `Settings` (ou `Preferences` no macOS).
3. No menu lateral, selecione `Plugins` e procure por **Checkstyle-IDEA**.
4. Instale o plugin e reinicie o IntelliJ IDEA se necessário.
5. Após reiniciar, abra `File` > `Settings` novamente.
6. No menu lateral, selecione `Tools` > `Checkstyle`.
7. Clique em `+` para adicionar uma nova configuração e selecione o arquivo de configuração (ex: `google_checks.xml` ou `sun_checks.xml`).
8. Defina essa configuração como "Default".
9. Observação: Pode também ser resgatado o arquivo de regras do Google [clicando aqui](https://raw.githubusercontent.com/checkstyle/checkstyle/master/src/main/resources/google_checks.xml).

## Verificação de Código com Checkstyle

Com o plugin configurado, você pode verificar seu código diretamente pelo IntelliJ:

- Clique com o botão direito sobre o diretório do projeto e selecione `Check Current File with Checkstyle`.
- Os resultados aparecerão em uma janela na parte inferior da IDE, indicando os problemas de estilo encontrados.

## Configuração das Regras de Estilo

Você pode utilizar arquivos de configuração padrões (como o `google_checks.xml`) ou criar um próprio. Aqui está um exemplo de trecho com algumas regras:

```xml
<module name="TreeWalker">
    <module name="Indentation">
        <property name="basicOffset" value="4"/>
        <property name="braceAdjustment" value="0"/>
    </module>
    <module name="LineLength">
        <property name="max" value="120"/>
    </module>
    <module name="FinalNewline"/>
</module>
```

## 💻 Exemplo de Código a Ser Estilizado

### Código Não Formatado
```java
public class Exemplo {
public static void main(String[] args) {
System.out.println("Olá, mundo!");
}
}
```


### Código Após Estilização com Checkstyle

```java
public class Exemplo {
    public static void main(String[] args) {
        System.out.println("Olá, mundo!");
    }
}
```

## 📜 Relatório de Erros do Checkstyle

Quando o Checkstyle encontra violações de estilo em seu código, ele gera um relatório como o seguinte:

```plaintext
Falta o comentário Javadoc. (1:1) [MissingJavadocType] <Estilo default>
Type name 'testes' must match pattern '^[A-Z][a-zA-Z0-9]*$'. (1:14) [TypeName] <Estilo default>
'method def modifier' tem um nível de indentação incorreto de 7. O nível esperado era o 2. (2:8) [Indentation] <Estilo default>
Falta o comentário Javadoc. (2:8) [MissingJavadocMethod] <Estilo default>
O filho de 'method def' está no nível de indentação incorreto de 8. O nível esperado era o 4. (3:9) [Indentation] <Estilo default>
'method def rcurly' tem um nível de indentação incorreto de 9. O nível esperado era o 2. (4:10) [Indentation] <Estilo default>
```

Esse relatório indica as seguintes violações:

- Falta de comentário Javadoc: O Checkstyle encontrou um tipo e método sem documentação Javadoc.

- Nome do tipo (classe) não segue a convenção: O nome da classe testes deve começar com uma letra maiúscula (padrão: ^[A-Z][a-zA-Z0-9]*$).

- Indentação incorreta: O Checkstyle apontou problemas de indentação, onde o código não está alinhado corretamente de acordo com as convenções.

## 🔧 Regras de Estilo Comuns
- Comprimento da linha: Garantir que as linhas de código não ultrapassem um determinado número de caracteres.

- Nomenclatura de variáveis: Garantir que variáveis e métodos sigam um padrão de nomenclatura (como camelCase para variáveis e métodos).

- Espaçamento: Certificar-se de que há espaços apropriados ao redor de operadores e vírgulas.

## 📜 Suprimindo Regras do Checkstyle com `@SuppressWarnings("checkstyle")`

Em alguns casos, você pode precisar ignorar uma ou mais violações específicas do Checkstyle, sem precisar alterar as regras no arquivo de configuração. Para isso, o Checkstyle permite o uso da anotação `@SuppressWarnings("checkstyle:regra")` para suprimir avisos de determinadas regras.

### Exemplo de Uso

Imagine que você tenha uma linha de código muito longa que ultrapassa o limite de comprimento de linha definido no Checkstyle, mas você deseja manter essa linha sem modificações. Para suprimir a violação dessa regra, você pode usar a anotação `@SuppressWarnings("checkstyle:LineLength")` como mostrado no exemplo abaixo:

```java
public class Exemplo {

    @SuppressWarnings("checkstyle:LineLength")
    public void exemploDeMetodo() {
        // Esta linha de código é longa, mas queremos ignorar a regra de comprimento de linha do Checkstyle
        String exemplo = "Este é um exemplo de linha de código extremamente longa que normalmente excederia o limite de comprimento de linha definido pelo Checkstyle.";
    }
}
```


## 📜 Conclusão

O Checkstyle é uma ferramenta essencial para desenvolvedores Java que desejam manter um código limpo, consistente e em conformidade com boas práticas de desenvolvimento. Com integração fácil ao IntelliJ IDEA, ele permite a aplicação automatizada de regras de estilo, promovendo legibilidade e manutenção no longo prazo.
