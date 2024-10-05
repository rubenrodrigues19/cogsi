# Introdução

Este projeto, desenvolvido no âmbito do Mestrado em Engenharia Informática do Instituto Superior de Engenharia do Porto, visa explorar o controlo de versões através da utilização do Git, uma ferramenta essencial na gestão de código em projetos colaborativos. Dividido em duas partes, o trabalho foca-se inicialmente na utilização da branch principal, sem ramificações, para a implementação de uma funcionalidade básica. Na segunda fase, é introduzida a criação e a gestão de branches para o desenvolvimento de novas funcionalidades e correção de erros.
Adicionalmente, o projeto desafia os alunos a proporem uma solução tecnológica alternativa ao Git, analisando comparativamente as suas características e implementando um design que possa cumprir os requisitos apresentados.
Os resultados deste trabalho serão documentados num ficheiro readme.md no repositório do grupo, com uma explicação detalhada dos passos e decisões tomadas durante o desenvolvimento, facilitando a sua reprodutibilidade.

# Tutorial
## 1º Passo - Criar o Repositório
Como ponto inicial, o primeiro objetivo é a criação do repositório para o desenvolvimento do projeto.

    git clone https://github.com/rubenrodrigues19/cogsi2425_1210693_1231423_1240490.git

Este comando faz uma cópia do repositório remoto especificado no GitHub para o teu computador, criando uma cópia local do projeto.

    echo " cogsi2425_1210693_1231423_1240490" >> README.md

Este comando adiciona o texto "cogsi2425_1210693_1231423_1240490" ao ficheiro README.md. Se o ficheiro não existir, ele será criado automaticamente. O README.md serve como um documento principal para descrever o projeto.

    git init

Inicializa um novo repositório Git no diretório atual, tornando-o um repositório Git local (caso ainda não tenha sido inicializado).
  
    git add README.md

Adiciona o ficheiro README.md à "staging area", preparando-o para ser incluído no próximo commit.

    git commit -m "Readme"

Este comando grava as mudanças registadas na "staging area" com uma mensagem de commit, neste caso, "Readme", descrevendo a alteração feita.

    git branch -M main

Muda o nome da branch atual (que, por defeito, pode ser master) para main, estabelecendo-a como a branch principal do repositório.

    git push -u origin main

Envia as mudanças locais (o commit feito anteriormente) para o repositório remoto (no GitHub), especificando a branch main como a branch para envio padrão no futuro.

## 2º Passo – Criar a Pasta CA1

Após se concluir o primeiro passo, o segundo objetivo é criar uma pasta (CA1) onde irá ser copiado e armazenado uma versão do projeto Building REST

    cd /caminho/para/o/repositório/local

Navega até o diretório local onde o repositório Git está armazenado. Este é o local onde a nova pasta CA1 será criada.

    mkdir CA1

Cria uma nova pasta chamada CA1 dentro do repositório local. Esta pasta será usada para organizar os ficheiros relacionados ao primeiro trabalho da disciplina.

    cp /caminho/de/origem/* /caminho/de/destino/CA1

Copia todos os ficheiros da origem especificada para a nova pasta CA1.
    
    git status

Exibe o estado atual do repositório, mostrando quais ficheiros foram modificados ou adicionados e estão prontos para levarem commit, ou se há ficheiros não rastreados.

    git add . 

Adiciona todos os ficheiros e alterações na pasta atual (neste caso, incluindo a nova pasta CA1 e os ficheiros dentro dela) à "staging area", preparando-os para o commit.

    git commit -m "Pasta CA1"

Grava um snapshot do estado atual dos ficheiros adicionados, com uma mensagem de commit descrevendo as alterações feitas. Aqui, a mensagem indica que a pasta CA1 foi criada e adicionada.
    
    git push -u origin main

Envia as alterações locais para o repositório remoto (GitHub), na branch main. O parâmetro -u define origin/main como o destino padrão para futuros git push, facilitando o envio de futuras alterações.

## 3º Passo - Criar Tag

Neste passo, o objetivo é desenvolver uma tag para marcar a primeira versão do projeto

    git tag 1.1.0

Este comando cria uma nova tag chamada 1.1.0 no repositório local. As tags são usadas para marcar versões específicas de um projeto, servindo como referências importantes. Neste caso, a tag 1.1.0 indica que esta versão é a primeira grande versão.

    git push origin 1.1.0

Este comando envia a tag 1.1.0 para o repositório remoto (GitHub). Assim, a tag criada localmente será também visível e acessível para qualquer pessoa que tenha acesso ao repositório remoto, marcando esta versão como um ponto importante do desenvolvimento.

    git fetch –tags

Este comando faz o download de todas as tags do repositório remoto para o repositório local. Garante que todas as tags remotas sejam atualizadas e disponíveis localmente.

## 4º Passo – Criação da Nova Feature (jobYears)

Ao longo deste ponto o objetivo é desenvolver a feature jobYears, para isso, deve ser adicionado um novo campo para registar os anos de serviço do empregado na empresa (por exemplo, jobYears). O suporte para este novo campo deve ser implementado, garantindo que apenas valores inteiros são permitidos. Além disso, devem ser criados testes unitários para validar a criação de empregados e verificar os seus atributos, assegurando que não há valores nulos ou vazios. Após a conclusão e testagem da nova funcionalidade, o código deve ser comprometido e enviado, seguido da criação de uma nova tag (ex.: v1.2.0).

![Imagem1](img/Imagem1.png)

Excerto do código utilizado para o desenvolvimento da feature.

![Imagem2](img/Imagem2.png)

Excerto do código dos testes unitários.

    git commit -m “1st Commit”
    git push -u origin main
    git tag -a 1.2.0 -m "Versão 1.2.0. - Parte 1"

Commit e implementação da Tag 1.2.0

## 7º Passo – Git Log

Neste ponto podemos ver os diferentes tipos de log e os seus outputs.
    
    git log –oneline

![Imagem3](img/Imagem3.png)

    git log --graph
    
![Imagem4](img/Imagem4.png)

    git log –pretty=format:”%h - %an <%ae> %ad : %s”
    
![Imagem5](img/Imagem5.png)

## 8º Passo – Revert

Neste passo, objetivo é voltar atrás um commit já feito criando assim um revert.

    git commit -m "Revert Test"
    git revert 2efbc828acd05996363bf7fca8b75cfbddc01d7c

O comando git revert 2efbc828acd05996363bf7fca8b75cfbddc01d7c reverte as alterações feitas no commit especificado pelo hash 2efbc828acd05996363bf7fca8b75cfbddc01d7c.
    
    git revert d38b0149c7b5c308630141427abd5bd141de5190 -m "Wrong Revert 1"
    git revert 1d4e5f318f9a44f97714893e400cc942c3c650f8

> **Nota**: Neste ponto executamos o comando revert mais vezes do que as necessárias, pois executamos incorretamente o comando, criando um revert que não era o nosso desejado, para corrigir o problema, fizemos outra sequencia de revert, a primeira para voltar ao ponto inicial e a segunda para irmos para o ponto desejado.

![Imagem6](img/Imagem6.png)

## 9º Passo – Criação de uma Nova Branch

Neste tópico, o objetivo é a criação de uma branch principal (main) que deve ser utilizada para publicar versões estáveis da aplicação "Building REST services with Spring". Cada nova funcionalidade deve ser desenvolvida numa branch com o nome da respetiva funcionalidade. As funcionalidades, após serem testadas, devem ser integradas na branch principal (main) para o lançamento de uma nova versão da aplicação.

    git status
    git add .
    
Verificar os ficheiros modificados e adicioná-los ao commit

    git branch “Branch Email-Field”

Este comando é utilizado para criar, listar ou eliminar branches no Git. No caso deste comando específico, é usado para criar uma nova branch.

    git commit -m 'Parte 2 - Branch Email-Field'
#
    git push --set-upstream origin email-field

Este comando envia a branch local email-field para o repositório remoto (GitHub), criando a branch também no GitHub, e define a branch remota origin/email-field como o "upstream" para a branch local. Isso significa que, no futuro, qualquer git push ou git pull na branch email-field será automaticamente associado a essa branch remota.
git checkout main
Este comando muda para a branch main no repositório local. Isso permite preparar a branch principal para fundir as alterações da branch email-field.
git merge email-field

