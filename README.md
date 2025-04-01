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

## 📜 Conclusão

O Checkstyle é uma ferramenta essencial para desenvolvedores Java que desejam manter um código limpo, consistente e em conformidade com boas práticas de desenvolvimento. Com integração fácil ao IntelliJ IDEA, ele permite a aplicação automatizada de regras de estilo, promovendo legibilidade e manutenção no longo prazo.
