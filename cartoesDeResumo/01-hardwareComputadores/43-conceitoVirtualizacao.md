# Virtualização – Conceitos, Exemplos e Procedimentos de Instalação 😃💻☁️

A ideia da virtualização surgiu para aproveitar melhor os recursos de hardware, especialmente em servidores, que muitas vezes ficam subutilizados. Com a virtualização, é possível simular o hardware usando um hypervisor, distribuindo de forma flexível os recursos para múltiplas Máquinas Virtuais (VMs).

---

## Conceitos Principais

### 1. Origem da Virtualização
- **Motivação:**  
  - **Subutilização de Recursos:**  
    Máquinas físicas, principalmente servidores, podem ficar ociosas em grande parte do tempo, desperdiçando CPU, memória e armazenamento.
- **Solução:**  
  - **Virtualização:**  
    Técnica que permite agrupar e particionar recursos físicos para criar diversas máquinas virtuais, aumentando a eficiência.
- **Emoticons:** 💡⏩💻

---

### 2. Como Funciona a Virtualização
- **Hypervisor:**  
  - Software (ou firmware) que “simula” o hardware e gerencia a distribuição de recursos para as VMs.
- **Distribuição de Recursos:**  
  - Cada VM recebe uma quantidade determinada de CPU, memória, e armazenamento conforme configurado.
- **Tipos de Virtualização:**
  - **Tipo 1 (Bare-Metal):**  
    - O hypervisor roda diretamente sobre o hardware, sem sistema operacional intermediário.
    - Exemplo: Uma máquina física com 8 núcleos de CPU, 16GB de RAM e 500GB de armazenamento pode dividir seus recursos entre VMs como:
      - **VM1:** 4 núcleos / 8GB RAM / 150GB
      - **VM2:** 2 núcleos / 4GB RAM / 50GB
      - **VM3:** 1 núcleo / 2GB RAM / 250GB  
    - **Vantagens:** Menor consumo de energia, redução de gastos com hardware e diminuição do espaço necessário no datacenter.
    - **Emoticons:** ⚙️🎯🚀
    
  - **Tipo 2 (Hosted):**  
    - O hypervisor roda sobre um sistema operacional já instalado na máquina física.
    - Exemplo: Em uma máquina física com 8 núcleos, 16GB de RAM e 500GB de armazenamento, VMs podem ser executadas sobre o Windows Server ou Linux Ubuntu.
    - **Emoticons:** 🖥️🔄

---

### 3. Exemplo Lúdico
Imagine que o seu servidor é um grande bolo 🍰.  
- Sem Virtualização:  
  - Você tem um bolo inteiro, mas apenas uma pequena fatia (um único serviço) está sendo consumida enquanto o resto fica parado.
- Com Virtualização:  
  - O bolo é cortado em várias fatias (VMs) para serem servidas a diferentes convidados, aproveitando cada pedaço e evitando desperdício.
- **Emoticons:** 🎂✂️😊

---

### 4. Exemplo Prático
Em uma empresa, um servidor físico com 8 núcleos, 16GB de RAM e 500GB de armazenamento é utilizado para rodar diversas aplicações críticas.  
- **Sem Virtualização:**  
  - Cada aplicação teria que rodar em um hardware dedicado, aumentando custos e consumo de energia.
- **Com Virtualização Tipo 1:**  
  - O hypervisor distribui os recursos para várias VMs, onde:
    - **VM1:** Hospeda um banco de dados robusto
    - **VM2:** Executa um servidor web
    - **VM3:** Gerencia serviços de backup e arquivos  
  - Assim, a empresa otimiza o uso do hardware, reduzindo custos operacionais e melhorando a eficiência energética.
- **Emoticons:** 🏢💰📈

---

## Procedimento de Pré-Instalação do Sistema Operacional (S.O.)

Antes de instalar o S.O. em uma VM ou em um ambiente físico, é necessário criar uma mídia de instalação:

- **Mídias de Instalação:**  
  - **DVD** ou **Pendrive** (mínimo 8GB, de boa qualidade, evitando pendrives falsificados).
- **Programas para Criação de Pendrive Bootável:**
  - **LinuxLive USB Creator**
  - **YUMI - Multiboot USB Creator**
  - **GNOME Multi-writer**
- **Imagens dos S.O.s:**
  - **Windows 10:** [Download Oficial da Microsoft](https://www.microsoft.com/pt-br/software-download/windows10)
  - **Ubuntu 23.10:** [Download Oficial do Ubuntu](https://ubuntu.com/download/desktop)
  - **Proxmox 8.0:** [Download Proxmox VE](https://www.proxmox.com/en/downloads/proxmox-virtual-environment)
- **Procedimento para Instalação:**
  - Inserir o pendrive com, por exemplo, a ferramenta Ventoy no computador.
  - Acessar a BIOS/UEFI (geralmente via tecla Del ou F2, dependendo do fabricante).
  - Alterar a sequência de boot ou selecionar a partição para boot rápido.
  - Selecionar a imagem do S.O. (ex.: Windows 10) e proceder com a instalação.
- **Emoticons:** 📀🔧💾

---

**Conclusão:**  
A virtualização surgiu para maximizar o uso de recursos de hardware e tem dois modelos principais — Tipo 1 (bare-metal) e Tipo 2 (hosted) — cada um com suas vantagens. Ela permite distribuir os recursos de um servidor físico para várias VMs, otimizando custos, energia e espaço. Além disso, preparar uma mídia de instalação correta é fundamental para a implementação eficiente do S.O., seja em um ambiente virtualizado ou físico. 😃💻☁️