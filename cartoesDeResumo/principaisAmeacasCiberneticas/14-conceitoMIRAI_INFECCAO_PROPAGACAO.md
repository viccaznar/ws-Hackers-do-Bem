# 🛡️ Estudo de Caso: Mirai - Infecção e Propagação

Este documento organiza os conceitos principais sobre a infecção e propagação do malware Mirai, explicando como ele identifica dispositivos vulneráveis, infeta, se comunica com o servidor de comando e controle (C2) e se propaga utilizando técnicas de brute force. Cada tópico inclui uma explicação fundamental, um exemplo lúdico e um exemplo prático.

---

## 1. Identificando Dispositivos Vulneráveis

**Fundamento:**  
- Mirai utiliza um scanner (vídeo em "scanner.c") que envia pacotes raw para endereços IP aleatórios (na porta 23 Telnet e outras) para identificar dispositivos que utilizam credenciais padrão (por exemplo, "root", "admin").  
- Ele armazena entradas de autenticação (via `add_auth_entry`) para testar essas combinações e detectar vulnerabilidades.

**Exemplo Lúdico:**  
Imagine um caçador que anda pelo bairro com um ímã gigante, procurando portas que não foram trancadas e se aproveitando dos "candidatos" que têm fechaduras fracas.  
🕵️‍♂️🔑

**Exemplo Prático:**  
Um código presente em Mirai testa automaticamente diversas combinações de nomes de usuário e senhas (como "root" com "888888" ou "admin" com "admin") em dispositivos conectados na rede, identificando aqueles que ainda usam configurações padrão.  
💻📡

---

## 2. O Processo de Infecção

**Fundamento:**  
- O processo começa com a inicialização do scanner, que prepara o ambiente, monta os pacotes SYN e os envia para endereços IP aleatórios em busca de respostas (SYN-ACK).  
- Se o dispositivo responde, o malware inicia ataques de brute force para tentar adivinhar as credenciais e, se for bem-sucedido, registra a conexão com o controlador.

**Exemplo Lúdico:**  
Imagine um ladrão que passeia pela vizinhança, batendo em portas abertas e tentando todas as chaves possíveis até encontrar aquela que abre a porta – esse é o ataque de brute force em ação.  
🚪🔍

**Exemplo Prático:**  
A máquina de estados no código do scanner envia pacotes e, ao receber um SYN-ACK de um dispositivo, começa a testar diversas combinações de usuário/senha até conseguir acesso, momento em que a infecção é confirmada e reportada.  
📧🔓

---

## 3. Estabelecimento da Comunicação com o C2

**Fundamento:**  
- Depois de infectar um dispositivo, o malware estabelece uma comunicação com um servidor de comando e controle (C2).  
- A função `resolve_cnc_addr` (em "main.c") realiza a resolução do domínio CNC, recebendo dados que orientam o ataque e possibilitam o controle remoto dos dispositivos comprometidos.

**Exemplo Lúdico:**  
Imagine um espião que, após se infiltrar em um prédio, ativa um telefone secreto para receber ordens do seu chefe – essa linha direta é o canal C2.  
📞🕵️‍♀️

**Exemplo Prático:**  
O código do Mirai utiliza técnicas de resolução de DNS para conectar-se com o C2. Uma vez conectado, o malware recebe instruções, como atualizar sua lista de alvos ou iniciar a exfiltração de dados, mantendo o controle sobre o bot infectado.  
🌐📡

---

## 4. Propagação e Natureza Autossustentável

**Fundamento:**  
- Após a infecção inicial, o malware propaga-se automaticamente, escaneando continuamente novos endereços IP em um loop.  
- A função `get_random_ip()` é utilizada para gerar destinos aleatórios, e o loop envia pacotes TCP SYN sem intervenção manual, permitindo que o malware se espalhe rapidamente.

**Exemplo Lúdico:**  
Pense em uma epidemia onde um vírus se espalha automaticamente, sem que seja necessário o contato direto entre cada pessoa – uma verdadeira "corrente infinita" de infecção.  
🔄🦠

**Exemplo Prático:**  
No loop infinito do scanner, o código envia milhares de pacotes por segundo para IPs aleatórios; se um dispositivo vulnerável for identificado, o malware tenta a autenticação automaticamente, ampliando sua rede de dispositivos comprometidos sem intervenção humana.  
💻🔀

---

## 5. Técnica de Brute Force

**Fundamento:**  
- A técnica de brute force consiste em tentar repetidamente combinações de senhas e usuários para quebrar a autenticação em dispositivos vulneráveis.  
- Esta abordagem explora o uso de credenciais padrão ou fracas, permitindo que o malware se infete com um esforço mínimo se as configurações de segurança não forem adequadas.

**Exemplo Lúdico:**  
Imagine um ladrão que tenta todas as chaves de um chaveiro até encontrar a que destranca uma porta – a persistência é a chave do brute force.  
🔑🔨

**Exemplo Prático:**  
O código lista várias combinações padrão de senhas (como "888888", "vizxv", "juantech") e testa cada uma delas. Um dispositivo que utiliza uma dessas senhas padrão é facilmente comprometido, permitindo ao atacante obter controle e, consequentemente, propagar o malware.  
📉✔️

---

## 6. Conclusão

**Resumo dos Conceitos:**  
- **Identificação de Dispositivos Vulneráveis:** Uso de scanners que testam credenciais padrão para detectar pontos fracos.  
- **Processo de Infecção:** Envio de pacotes SYN, resposta SYN-ACK e tentativa de autenticação via brute force.  
- **Comunicação com C2:** Estabelecimento de canais para controle remoto e atualização de comandos.  
- **Propagação Autossustentável:** Loop contínuo que busca novos alvos utilizando IPs aleatórios.  
- **Técnica de Brute Force:** Exploração sistemática de senhas fracas até obter acesso.

🌟 Em suma, compreender a infecção e propagação do Mirai – desde a identificação de dispositivos vulneráveis até a comunicação com o C2 e o uso de técnicas de brute force – é essencial para desenvolver estratégias de defesa eficazes, proteger redes e mitigar danos causados por botnets.  
🚀🔐