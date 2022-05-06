# Exercícios segunda parte lab redes

1) Qual a função da camada de enlace de dados?
    
    A segunda camada do modelo OSI tem a função de dar um significado para os dados, essa camada possúi algumas funções: detectar e corrigir erros que possam acontecer na camada 1 tanto por falhas fisícas ou lógicas, delimita e valida os quadros transmitidos, estabelecer um protocolo de comunicação entre sistemas diretamente ligados atribuindo o MAC address de trasnmissão e recepção.. Resumindo essa camada faz o controle/validação dos quadros sendo transmitidos, controla o fluxo para que um transmissor com maior velocidade transmita em uma velocidade que o receptor suporte. 

   **Principais dispositivos que trabalham nessa camada**: SWITCHS e BRIDGES
2) Como ela é subdividida?

   **Controle de Link lógico**: Essa camada faz a tradução e determina qual o protocolo estará atuando na camada de rede. ela determina para onde aquele quadro deverá ser destinado, essa camada tambem pode fornecer o controle d eflxo e sequecencia de bits do controle.
   
   **Controle de acesso ao meio (MAC)**: Faz o controle do enderaçamento por ip MAC adicionando o header que contem o endereço de recepção, faz a notificação de erros e controle de fluxo e a ordem em que os quadros serão enviados.

3) O que é o padrão Ethernet?

   É um padrão padrão de interconexão de redes locais, foi criado em 1972 nos laboratórios da Xeros. criado com o intuito de padronizar os modelos de redes, foi homologado ao IEEE em 1980, em 1987 a ISO aprovou com denominação ISO 8802. Esse padrão consiste de três elementos: meio físico, regras de controle de acesso ao meio e o quadro enthernet. ele define como os dados serão transmitidos através dos cabos de rede. com função de agrupar os dados entregues pelos protocolos de alto nível (TCP/IP por exemplo) e inseri-los dentro dos quadros que serão enviados. esse padrão determina a camada física e camada de enlace que opera de forma síncrona em 10Mbps, com quadros com o tamanho variável entre 64 e 1518 bytes. Originalmente criado para operar numa topologia em barramento, funcionando em broadcast.
4) Explique cada um dos campos que formam o padrão IEEE 802.3
   ## IEEE 802.3 
   | 7      | 1 | 6             | 6            | 2    | 46-1500 | 4 | 
   |--------|---|---------------|--------------|------|---------|---|
   |Preamble|SOF|Destin. address|Source address|length|802.2 PDU|FCS|
 
   ## Ethernet
   | 8      | 6                 | 6            | 2  |46-1500|4  |
   |--------|-------------------|--------------|----|-------|---|
   |Preamble|Destin. address    |Source address|type|Data   |FCS|

    - Preamble/SOF: Estabelecer o sincronismo entre transmissor e receptor é o delimitador de início de quadro, também chamado de início de quadro, são usados para sincronização entre os dispositivos de envio e recebimento. os primeiros bytes informam aos receptores para se prepararem para receber um novo quadro.
   - Endereço de destino...
   - Endereço de origem...
   - Length: Tamanho do quadro.
   - Data/802.2 PDU: dado sendo transmitido.
   - FCS: É usado para a verificação do quadro, ele usa uma verificação de redundância cíclica. ele faz a soma dos valores dos valores contidos no data.
5) O Que é a agregação de Link?
   
   Padrão IEEE 802.3ad é quando utilizamos mais de uma conexão em um único fluxo de transmissão de dados entre switchs.
6) Para que serve o STP?

    É um protocolo para equipamentos de redes que permite resolver problemas de loop em redes comutadas cuja a topologia introduza anéis nas ligações, auxiliando na melhor performance da rede.
7) Quais são os possíveis status de uma porta no contexto do STP?

    - Bloqueio: apenas recebendo BPDUs.
    - Escuta: O switch processa BPDUs e espera por possíveis novas informações que podem fazê-lo voltar ao estado de Bloqueio.
    - Aprendizado: Quando a porta ainda está "aprendendo" e montando sua tabela de endereços de origem dos frames recebidos.
    - Encaminhamento: A porta envia e recebe dados. Operação normal. O STP continua monitorando por BPDUs que podem indicar que a porta deve retornar ao estado de bloqueio prevenindo um loop.
    - Desativado: Não está utilizando STP. O administrador de redes pode desabilitar a porta manualmente.
8) O que é uma VLAN?

    Uma rede local virtual, normalmente denominada de VLAN, é uma rede logicamente independente. várias VLANs podem coexistir em um mesmo comutador, de forma a dividir uma rede local em mais de uma rede.
9)  Quais são os tipos?

    - Baseada em portas
    - Baseada em endereço MAC
    - Em tipo de protocolo
    - Faixas de IP de subrede
    - Camadas superiores
10) Explique cada um dos campos que compõem um quadro 802.1Q.
    ## Traditional Ethernet data frame
    | 6 bytes    | 6 bytes | 2 bytes | 46-1500 bytes | 4 bytes |
    |------------|---------|---------|---------------|---------|
    |Destination Address|Source address|Length/Type|Data|FCS   | 

    ## VLAN data frame
    |6 bytes|6 bytes|4 bytes|2 bytes|46-1500 bytes|4 bytes|
    |-------|-------|-------|-------|-------------|-------|
    |Destination address|Source address|VLAN Tag|Length/type|Data|FCS|

    ### VLAN Tag
    |2 bytes|3 bits|1 bit|12 bits|
    |-------|------|-----|-------|
    |TPID   | PRI  | CFI | VID   |
