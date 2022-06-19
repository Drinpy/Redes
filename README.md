# Redes 
   
##### `01/06/22`

### Camadas de aplicação
</br>

#### `RTT:` (Round Trip Time) --> Pág 75 do Livro [Kurose | Ross]

###### - Medida de tempo "ida e volta"

#### `Paralelismo:` Não há necessidade de esperar o pacote ser lido por completo para poder enviar outro, dessa forma múltiplos pacotes podem ser iniciados.
</br>

#### HTTP/2: Stream, Mensagem, Frame.

---

##### `02/06/22`

#### HTTP Métodos: POST/HEAD/PUT/DELETE

#### `Comunicação SMTP` pode cair em provas.
###### - Utiliza protocolo TCP porta(25)

#### `POP3`
###### - Utiliza protocolo TCP porta(110)


---

##### `03/06/22`

### Protocolo HTTP
</br>

#### - A aba de pesquisa do Google usa GET em vez de POST, pois, GET permite Bookmark. O POST ainda poderia ser utilizado, porém, sem a possibilidade de Bookmark.
#### - Pode-se analisar o url e perceber que é usado GET ("?" + Parâmetros)
#### - Quando o URL é muito extenso é preferível usar POST.
#### - Nomes de usuário e senha também podem ser enviados pelo GET, mas quando enviados, são criptografados na URL.

</br>

### Formato da mensagem HTTP
#### `Resquest:`
<p
   
![Screenshot from 2022-06-03 10-47-26](https://user-images.githubusercontent.com/66181571/171866978-45d2f678-0066-429e-9b46-d6460de005ed.png)
   
![Screenshot from 2022-06-03 10-47-35](https://user-images.githubusercontent.com/66181571/171867352-296044e0-a0a5-4148-905f-72d6556af8fb.png)

</p>

#### `Response:`
<p

![Screenshot from 2022-06-03 10-52-02](https://user-images.githubusercontent.com/66181571/171867720-4ba2f77d-0463-46e3-95bd-9a0279b8fd7a.png)
   
![Screenshot from 2022-06-03 10-52-13](https://user-images.githubusercontent.com/66181571/171867746-c13e37eb-156b-4a73-9035-70995ae064d2.png)

   
</p>

</br>

### Códigos HTTP Response
#### `301:` Em resumo serve para redirecionamento. (Oculto no URL, mas visível no "Telnet" do terminal)
#### `400:` Bad request, ou seja, a requisição não foi entendida pelo servidor.
#### `404:` Destino não encontrado! (No "Telnet" o comando 'GET /"Url inexistente" / HTTP/1.1' apresenta a mensagem 404)

</br>

#### Em um site é bom ter uma ferramenta que analisa a taxa de acesso do próprio site, ademais uma ferramenta que edita as permissões do acesso para que não tenha uma excesso de requisições por um mesmo usuário. (Por exemplo: Bots)

<a href="https://http.cat/"> Códigos HTTP Response resumidamente.</a>

</br>

##### `Procurar sobre "Postman"`

</br>

---

##### `06/06/22` - Data de postagem!

Material feito por: <a href="https://github.com/SprigganCS"> SprigganCS </a>

### Atrasos 

<p> Diferença entre atraso de transmissão e propagação. 

Atraso de transmissão está relacionado ao tempo de converter a informação em onda de rádio ou em energia. Depende da largura de banda. 

Atraso de propagação está relacionado a distância (como a distância que uma onda precisa percorrer de um ponto a outro). 
</p>



#### PC -> Roteador (transmissão) -> (propagação) -> Outro roteador 

<p> - Atraso de propagação = d/s </p>


`D` = distância entre roteadores 

`S` = velocidade de propagação no meio 

#### `Atraso total = Aprocessamento + Afila + Atransmissão + Apropagação` 


- Atraso de processamento tipicamente são poucos microsegundos 

- Atraso de fila depende do congestionamento 

- Atraso de transmissão = L/R, significativo para links de baixa velocidade 

- Atraso de propagação varia de poucos microsegundos a centenas de segundos 
</br>

### Camadas 

<ui>
   
<li> Aplicação - http, pop3, imap, dns, smtp, dhcp, ftp 

<li> Transporte – TCP, UDP 

<li> Rede – IP, BGP, IGP, OSPF, ICMP 

<li> Enlace – Wifi, Ethernet 

<li> Física - Bits "nos fios"
   
</ui>

#### (Quanto mais para cima na lista, mais próximo ao usuário). 


</br>

### Portas 
   
<p>
Um número de porta é associado a um único processo (gerado por um programa em execução). 

Nº de porta <1024 são reservadas (http, https, ssh, etc) 

Nº de porta >=1024 são chamadas alfas e podem ser usadas.
   
</p>
 

#### O número de porta utilizado por um processo no PC cliente (geralmente alfa, pois muitas abas podem estar abertas num navegador) se liga a uma porta (geralmente reservada) do servidor, por esse motivo que os números de portas em cada ponta é diferente. (Segundo o professor pode ser igual, mas conceitualmente é estranho). 

</br> 

### Protocolos de transporte 

#### `TCP` 

<ui>
   
<li>É um tipo de serviço orientado à conexão. Ele é mais lento, mas consegue transportar mais recursos, informações longas como páginas html, arquivos de estilo, etc. 

<li>Se houver perda de dados no caminho (perda de pacote), ele recupera automaticamente. 

<li>Uma quantidade de memória é usada para armazenar informações necessárias. 

<li>É garantido que a informação transmitida é recebida pelo usuário, por esse motivo é mais seguro. 

<li>As informações chegam ordenadas. 

<li>Possui controle de fluxo e de congestionamento. O controle de fluxo evita que o buffer de destino fique cheio. 

</ui>

#### `UDP`

<ui>
   
<li> É outro tipo de serviço, que funciona com os recursos mínimos. 

<li> DNS é um exemplo que funciona com o protocolo UDP. 

<li> Se houver perda, os dados são perdidos, e uma nova requisição deve ser feita a partir da aplicação. 
 
<li> Não há garantia que a informação transmitida será recebida pelo usuário. 

<li> As informações podem chegar em ordem diferentes da saída. 

<li> A vantagem em se utilizar o UDP é que é mais rápido. 

<li> O UDP não inclui sistema de controle de congestionamento. 

<li> UDP funciona em tempo real. 

</ui>
 
</br>
 
`Socket e portas são sinônimos. `


#### `DNS:` Sistema de nome de domínio, é como uma lista que contém as URLs (facil de decorar) relacionado com um ip (endereço) dos sites. Quando o usuario entra num site pelo url, o Resolver manda essa string para o Recursivo (servidor disponibilizado pelos provedores de internet), o recursivo possui uma lista com os ip's, mas caso a URL requisitada nunca tenha sido acessada pelos usuários anteriormente, ele pede para o servidor raíz localizar, que por sua vez pergunta aos servidores autoritativos. Até que o ip do site seja localizado em algum servidor. Então esse endereço retorna com o ip do servidor e a porta que aquela página HTML está localizada. 

 </br>

`A comunicação pode ser feita de 3 formas: cliente/servidor, P2P (peer to peer) ou híbrida.` 

 
#### `Cliente/servidor:` O cliente entra numa url, o Recursivo retorna o IP e a porta daquele HTML(UDP), agora a ponta do usuário sabe onde requisitar o HTML, que vai ser enviado pelo servidor pelo protocolo TCP. 

##### Outro modelo cliente/servidor é com um balanceador, que permite que os servidores se mantenham ocultos ao usuário. Um único balanceador se conecta a vários servidores por uma rede privada. 

 
`P2P:` Mais raro, a conexão é direta sem intermédio de um servidor. 

`Híbrido:` Servidor é essencial para o funcionamento, mas os clientes podem se comunicar diretamente.

</br>

---

##### `07/06/22` Estudo

#### Protocolo de aplicação define:
<ui>
   <li> Os tipos de mensagens trocadas, por exemplo, requisição e de resposta.
   <li> A sintaxe de vários tipos de mensagens, tais como os campos da mensagem e como os campos são delineados.
   <li> A semântica dos campos, isto é, o significado da informação nos campos.
   <li> Regras para determinar quando e como um processo envia mensagens e responde mensagens.    
</ui>

#### HTTP define como os clientes requisitam páginas aos servidores e como eles as transferem aos clientes.

#### `Socket:` É a interface entre a camada de aplicação e a de transporte dentro de um hospedeiro.
##### - "Analogamente a porta de uma casa."

`*HTTP é um protocolo sem estado, pois, não mantém informação alguma sobre o cliente.`

</br>

---

##### `08/06/22`

#### `DNS local` = RECURSIVO.
##### - Os demais ligados são ITERATIVOS como por exemplo: .root, .br, .edu.
##### ` Entre o computador e o servidor DNS local a consulta é Recursiva.`

</br>

---

##### `18/06/22`

### <li> Camada de transporte </li>
#### A camada de transporte da Internet c arrega mensagens da camada de aplicação entre os lados do cliente e servidor de um aplicação.
### <li> Camada de rede </li>
#### A camada de rede da Internet é responsável pela movimentação, de um hospedeiro para outro, de pacotes da camada de rede, conhecidos como `datagramas`. O protocolo de camada de transporte da Internet (TCP ou UDP) em um hospedeiro de origem passa um segmento da camada de transporte e um endereço de destino à camada de rede, exatamente como você passaria ao serviço de correios uma carta com um endereço de destinatário. `A camada de rede então provê o serviço de entrega do segmento à camada de transporte no hospedeiro destino.` Essa camada inclui o famoso IP, que define os campos no datagrama e o modo como os sistemas finais e os roteadores agem nesses campos. Existe apenas um único protocolo IP, e todos os componentes da Internet que têm uma camada de rede devem executá-lo. Embora a camada de rede contenha o protocolo IP e também numerosos outros de roteamento, ela quase sempre é denominada apenas camada IP, refletindo o fato de que ele é o elemento fundamental que mantém a integridade da Internet.
