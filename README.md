# design-walter

🔹 Abstração
A abstração consiste em representar elementos do mundo real dentro do software. Em Java, por exemplo, é comum utilizar classes no pacote entity para modelar entidades que refletem os dados armazenados no banco de dados.

🔹 Princípios de Projeto de Código
Boas práticas são diretrizes que orientam o desenvolvimento de software. O objetivo é tornar o sistema mais simples de compreender, manter e evoluir, aplicando conceitos como abstração, modularização, baixo acoplamento e alta coesão.

Organização por Camadas:

Controller = API Rest / HTML
Entity = Dados
Repository = con bd
Service = Lógica
Config = Centraliza as configurações das aplicações
🔹 Padronização de Código


🔹 Ocultamento de Informação
Também conhecido como encapsulamento, consiste em ocultar os detalhes internos de uma classe e disponibilizar apenas o que for essencial. Dessa forma, evita-se que outras partes do sistema dependam diretamente da implementação interna. Geralmente, isso é feito declarando os atributos como private e permitindo o acesso por meio de métodos get e set.

🔹 Coesão
Está relacionada ao quanto os elementos de uma classe ou módulo trabalham em torno de uma única responsabilidade. Quanto maior a coesão, mais clara e organizada é a estrutura do código, o que facilita sua compreensão.

🔹 Acoplamento
Mede o nível de dependência entre classes ou módulos. O ideal é manter um baixo acoplamento, para que cada parte do sistema funcione de forma independente, o que facilita tanto a manutenção quanto a possibilidade de reaproveitar o código em outros contextos.

🔹Classe Anêmica
É uma classe que contém apenas atributos, seus respectivos getters e setters, mas não possui comportamento (métodos com regras de negócio).
🔹 Exemplo: uma classe Livro que só tem titulo, autor e preço, mas não possui métodos como aplicarDesconto() ou calcularImposto().

Diagrama UML

Flecha Vazia Contínua (Herança): Representa especialização. Exemplo: “Gato é um Mamífero”.

Flecha Vazia Pontilhada (Interface): Representa implementação de contrato. Exemplo: “PagamentoOnline implementa MétodoPagamento”.

Flecha Preenchida Contínua (Associação): Representa relação de uso. Exemplo: “Motor faz parte de Carro”.

Débito Técnico
Refere-se a escolhas de implementação rápidas ou inadequadas que facilitam no curto prazo, mas podem gerar falhas ou dificultar a manutenção no futuro.
🔹 Exemplo: duplicar trechos de código em vários lugares em vez de criar um método reutilizável.

SOLID
O objetivo dos princípios SOLID é aplicar corretamente a Programação Orientada a Objetos, garantindo código mais coeso, desacoplado e flexível.

🔹 Exemplo:

S (Single Responsibility): Uma classe RelatorioPDF deve apenas gerar relatórios, não salvar em banco.

O (Open/Closed): Um método de cálculo de frete deve aceitar novas regras sem modificar o código existente.

L (Liskov Substitution): Uma subclasse Quadrado deve poder substituir Retangulo sem quebrar o sistema.

I (Interface Segregation): Uma interface Veiculo não deve obrigar bicicleta a implementar abastecer().

D (Dependency Inversion): Em vez de a classe Loja depender de CartaoCredito, ela deve depender de uma abstração MetodoPagamento.

🔹 S - Single Responsibility Principle
O Princípio da Responsabilidade Única (Single Responsibility Principle) diz que uma classe deve ter apenas um motivo para mudar, ou seja, deve ser responsável por apenas uma coisa dentro do sistema. Quando uma classe assume várias responsabilidades, ela fica mais difícil de entender, testar e manter. Seguindo esse princípio, cada classe foca em uma tarefa específica, deixando o código mais organizado e facilitando futuras alterações.

🔹 I - Interface Segregation Principle
O Princípio da Segregação da Interface (Interface Segregation Principle) afirma que uma classe não deve ser obrigada a implementar métodos que não utiliza. Em vez de criar interfaces muito grandes e genéricas, é melhor dividi-las em interfaces menores e mais específicas, para que cada classe implemente apenas o que realmente faz sentido para ela. Isso evita código desnecessário e torna o sistema mais organizado e fácil de manter.

Arquitetura MVC (Model-View-Controller) É uma arquitetura utilizada para organizar melhor projeto, dividindo suas responsabilidades.

M = Model = Dados da aplicação / Entidade
V = View = Interface
C = Controller = Intermediário entre o View e Model, organizando as informações, recebendo as informações dos usuários, depois chamando as partes certas do Model para resolver e entrega o resultado para o View.
Swing - Janela em JAVA

package br.univille;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JOptionPane;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;


public class Janelinha extends JFrame{

    private JButton botaozinho;
    private Controlador controlador;

    public Janelinha() {
        setTitle("Eu nao acredito");
        setSize(500,500);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        botaozinho = new JButton("ME CLICA");
        controlador = new Controlador();
        botaozinho.addActionListener(controlador);

        /*botaozinho.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                JOptionPane.showMessageDialog(null,"oi");
            }
        });*/
        
        add(botaozinho);

        setVisible(true);
    }
    public static void main(String[] args) {
        new Janelinha();
    }
}
🔹 Princípio da inversão de dependências
O Princípio da Inversão de Dependências afirma que módulos de alto nível não devem depender diretamente de módulos de baixo nível, mas sim de abstrações. Em outras palavras, em vez de uma classe depender de outra classe concreta, ela deve depender de interfaces ou contratos. Isso torna o sistema mais flexível e facilita mudanças, já que você pode trocar implementações sem alterar o código principal.

🔹 Prefira composição a herança
Significa que é melhor construir funcionalidades combinando objetos (composição) do que depender fortemente de heranças de classes. A herança pode criar estruturas rígidas e difíceis de manter, enquanto a composição permite maior reutilização de código e flexibilidade para montar comportamentos diferentes.

🔹 Princípio de Demeter (menor conhecimento)
É um conceito de design de software que busca reduzir o acoplamento entre os módulos ou classes de um sistema, evitando a utilização de variáveis globais

🔹 Princípio Aberto/Fechado
Princípio Aberto/Fechado diz que uma entidade de software (como uma classe ou módulo) deve estar aberta para extensão, mas fechada para modificação. Isso quer dizer que, quando precisarmos adicionar novas funcionalidades, devemos fazê-lo estendendo ou adicionando código, e não mudando diretamente o que já funciona. Assim, evitamos quebrar funcionalidades existentes e mantemos o sistema mais seguro para evoluir.

Aberto: Adicionar funcionalidades novas sem mexer no que já foi feito, preservando a estabilidade do sistema.
Fechado: Evita alterações que podem gerar novos bugs.
Abstrações em Java:

Classe = Contém atributos e métodos.
Interface = Define um contrato (métodos sem implementação).
Classe Abstrata = Mistura classe e interface; já traz parte do código pronto, mas exige que os métodos abstratos sejam implementados pelos filhos.
@autowired É usado para diminuir acoplamento, evitando que uma classe implemente em outra classe.

Solid
🔹 L - Liskov Substitution Principle
Liskov garante que uma classe filho possa ser usada como se fosse a classe pai, sem surpresas. Isso mantém o código mais previsível e seguro para alterações futuras.

🔹 Design Patterns
São soluções reutilizáveis para problemas recorrentes no desenvolvimento de software. Foram popularizados pelos "Gang of Four" (Erich Gamma, Richard Helm, Ralph Johnson e John Vlissides) em 1994.
Categorias
No livro existem 23 padrões, divididos em três categorias:

Criacionais: soluções para criação de objetos. Exemplos: Abstract Factory, Factory Method, Singleton, Builder, Prototype.

Estruturais: soluções para composição de classes e objetos. Exemplos: Proxy, Adapter, Facade, Decorator, Bridge, Composite, Flyweight.

Comportamentais: soluções para interação e divisão de responsabilidades. Exemplos: Strategy, Observer, Template Method, Visitor, Chain of Responsibility, Command, Interpreter, Iterator, Mediator, Memento, State.

🔹 Factory Method
Suponha um sistema distribuído baseado em TCP/IP. Três funções (f, g, h) criam objetos TCPChannel para comunicação:

void f() {
  TCPChannel c = new TCPChannel();
  ...
}

void g() {
  TCPChannel c = new TCPChannel();
  ...
}

void h() {
  TCPChannel c = new TCPChannel();
  ...
}

Problema
Se for necessário usar UDP, o sistema quebra o Princípio Aberto/Fechado.
O código não está preparado para extensões sem modificações.

Solução
Criar um método fábrica estático que centralize a criação dos objetos:

class ChannelFactory {
  public static Channel create() { // método fábrica estático
    return new TCPChannel();
  }
}

void f() {
  Channel c = ChannelFactory.create();
  ...
}

void g() {
  Channel c = ChannelFactory.create();
  ...
}

void h() {
  Channel c = ChannelFactory.create();
  ...
}
Agora, se o canal mudar para UDP, apenas o método create da ChannelFactory precisa ser alterado.
Fábrica Abstrata
Uma variação utiliza uma classe abstrata para definir vários métodos fábrica:

abstract class ProtocolFactory { // Fábrica Abstrata
  abstract Channel createChannel();
  abstract Port createPort();
  ...
}

void f(ProtocolFactory pf) {
  Channel c = pf.createChannel();
  Port p = pf.createPort();
  ...
}
🔹 Singleton
Suponha uma classe Logger usada para registrar operações do sistema:

void f() {
  Logger log = new Logger();
  log.println("Executando f");
}

void g() {
  Logger log = new Logger();
  log.println("Executando g");
}

void h() {
  Logger log = new Logger();
  log.println("Executando h");
}
O problema é que criamos múltiplas instâncias do Logger, o que não é eficiente nem desejável.

Solução
Aplicar o padrão Singleton, garantindo que a classe possua apenas uma única instância global:

public class Logger {
    private static Logger instance;

    private Logger() {}

    public static Logger getInstance() {
        if (instance == null) {
            instance = new Logger();
        }
        return instance;
    }

    public void println(String msg) {
        System.out.println(msg);
    }
}

// Uso
Logger log = Logger.getInstance();
log.println("Executando f");
🔹 Observer
O Observer define uma relação de dependência um-para-muitos entre objetos.
Quando um objeto muda de estado, todos os dependentes são notificados automaticamente.

Exemplo prático: sistemas de eventos e notificações.

Estrutura
Subject = objeto observado.
Observer = interessados que “escutam” mudanças no subject.
Exemplo em Java
// Interface Observer
public interface Observer {
    void update(String message);
}

// Subject
import java.util.ArrayList;
import java.util.List;

public class Publisher {
    private List<Observer> observers = new ArrayList<>();

    public void addObserver(Observer o) {
        observers.add(o);
    }

    public void notifyObservers(String message) {
        for (Observer o : observers) {
            o.update(message);
        }
    }
}

// Concrete Observer
public class Subscriber implements Observer {
    private String name;

    public Subscriber(String name) {
        this.name = name;
    }

    public void update(String message) {
        System.out.println(name + " recebeu: " + message);
    }
}

// Uso
public class Main {
    public static void main(String[] args) {
        Publisher publisher = new Publisher();

        Subscriber s1 = new Subscriber("Alice");
        Subscriber s2 = new Subscriber("Bob");

        publisher.addObserver(s1);
        publisher.addObserver(s2);

        publisher.notifyObservers("Novo artigo publicado!");
    }
}
🔹 Conclusão
Padrões de Projeto são fundamentais para desenvolver sistemas mais flexíveis e reutilizáveis. Eles auxiliam tanto no próprio processo de desenvolvimento quanto na compreensão de sistemas criados por terceiros. Os principais grupos são Criacionais, Estruturais e Comportamentais, com exemplos práticos como Factory, Singleton e Observer.

🔹 Expectativas de um arquiteto
No livro Fundamentos da Arquitetura de Software – Introdução, os autores ressaltam que as responsabilidades de um arquiteto de software vão além da habilidade técnica. Esse profissional precisa tomar decisões estruturais relevantes, facilitar a comunicação entre equipes de desenvolvimento, operação e negócios, e assegurar que o sistema atenda não apenas às funcionalidades previstas, mas também a requisitos de qualidade como desempenho, escalabilidade e segurança.
🔹 Decisões de arquitetura
As decisões de arquitetura são consideradas críticas, pois moldam a estrutura do sistema e impactam diretamente sua capacidade de evolução. Essas escolhas envolvem estilos arquiteturais, padrões, frameworks, tecnologias e trade-offs, que devem ser cuidadosamente avaliados, já que se tratam de definições difíceis de modificar após implementadas. O arquiteto é responsável por equilibrar necessidades técnicas e estratégicas ao tomar tais decisões.

🔹 Analisar continuamente a arquitetura
Outro ponto fundamental do papel do arquiteto é a análise contínua da arquitetura. Isso significa revisar periodicamente se a estrutura do sistema ainda atende às demandas atuais do negócio e às necessidades de qualidade. O arquiteto deve identificar pontos de melhoria, ajustar decisões e garantir que a arquitetura continue relevante e eficaz diante das mudanças no mercado e na tecnologia.

🔹 Manter-se atualizado
Os autores reforçam também a importância de o arquiteto manter-se atualizado. A área de tecnologia evolui rapidamente, e um profissional que não acompanha novas práticas, linguagens, frameworks e tendências corre o risco de propor soluções ultrapassadas que comprometam a longevidade do sistema. Estar em constante aprendizado é, portanto, essencial para garantir decisões assertivas e alinhadas com o estado da arte.

🔹 Domínio do negócio
Por fim, o domínio do negócio é apresentado como requisito indispensável. O arquiteto de software não pode atuar de forma isolada apenas no campo técnico; ele deve compreender os objetivos, processos e prioridades da organização. Esse entendimento permite alinhar a arquitetura às metas estratégicas do negócio, garantindo que as soluções técnicas ofereçam valor real e sustentem os resultados desejados pela empresa.

🔹 DevOps
DevOps é uma abordagem que integra as equipes de Desenvolvimento (Dev) e Operações (Ops) para melhorar a colaboração e a produtividade. Em vez de trabalhar em silos, as equipes compartilham práticas e ferramentas para planejar, desenvolver, testar, implantar e monitorar aplicativos de forma contínua e eficiente.

Por que utilizar DevOps
Adotar práticas de DevOps pode trazer diversos benefícios para as organizações:

Redução do tempo de ciclo: Ao trabalhar em lotes menores e automatizar processos, é possível entregar software mais rapidamente.

Melhoria contínua: Com feedback constante, as equipes podem aprender e melhorar seus processos.

Maior colaboração: A integração entre desenvolvimento e operações promove uma comunicação mais eficaz.

Maior estabilidade: A automação e o monitoramento constante ajudam a identificar e corrigir problemas rapidamente.

🔹 Diferença entre: Arquitetura e Design
Rrquitetura de software é responsável pelas decisões estruturais mais importantes de um sistema, aquelas que têm impacto direto na sua qualidade, evolução e manutenção. Ela envolve escolhas de estilos arquiteturais, padrões, tecnologias e trade-offs que são difíceis de mudar depois de implementados. Já o design de software se concentra em decisões de nível mais baixo, voltadas à organização interna de componentes, classes e métodos. Essas decisões são mais fáceis de modificar e lidam com os detalhes da implementação, garantindo clareza e coesão no código.

🔹 Formação do conhecimento de um arquiteto modelo T?
A formação de um arquiteto de software deve seguir o conceito do profissional em “T”. A barra horizontal do T representa o conhecimento amplo, que envolve transitar por diversas áreas como linguagens de programação, bancos de dados, nuvem, DevOps, segurança e redes, possibilitando compreender o sistema como um todo e dialogar com diferentes equipes. Já a barra vertical do T simboliza o conhecimento profundo, ou seja, a especialização em algumas áreas específicas, como microsserviços, performance ou segurança, permitindo que o arquiteto seja referência técnica nesses pontos críticos. Essa combinação entre amplitude e profundidade torna o arquiteto mais completo e preparado para tomar decisões estratégicas.

🔹 Trade-off
Trade-off é o processo de avaliar as consequências de escolher uma alternativa em detrimento de outra dentro da arquitetura de software. Cada decisão arquitetural envolve ganhos e perdas, e cabe ao arquiteto analisar cuidadosamente essas trocas para equilibrar prioridades como desempenho, segurança, escalabilidade, custo, manutenibilidade e prazo de entrega.

Não existe solução perfeita: toda escolha traz benefícios em alguns aspectos, mas também impõe limitações em outros. Por exemplo, adotar uma arquitetura de microsserviços pode oferecer maior escalabilidade e flexibilidade, porém aumenta a complexidade operacional e os custos de monitoramento.

A análise de trade-offs deve considerar o contexto do negócio, os requisitos de qualidade e as restrições existentes, levando em conta impactos de curto e longo prazo. Assim, um arquiteto eficiente não busca eliminar os trade-offs, mas sim tomar decisões conscientes e justificadas, comunicando de forma clara às partes interessadas os motivos das escolhas e os compromissos envolvidos.
