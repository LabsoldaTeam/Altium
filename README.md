# Guia de Organizacao das Bibliotecas Altium (Master)

Esta pasta foi estruturada para ser a base unica, limpa e padronizada das bibliotecas de Altium da equipe, facilitando tanto o trabalho offline quanto a futura sincronizacao em nuvem ou rede.

---

## Estrutura de Pastas
```
D:\Altium_Libraries_Master\
|-- 01_Bibliotecas_Integradas/              <- Arquivos .IntLib compilados prontos para instalar e usar em projetos
|   |-- Capacitores_PTH.IntLib
|   |-- Capacitores_SMD.IntLib
|   |-- Resistores_PTH.IntLib
|   |-- Resistores_SMD.IntLib
|   |-- CIs.IntLib
|   |-- Conectores.IntLib
|   |-- Contatos.IntLib
|   |-- Diodos.IntLib
|   |-- Indutores.IntLib
|   |-- Leds.IntLib
|   |-- Modulos.IntLib
|   |-- Reles.IntLib
|   |-- Serigrafias.IntLib
|   `-- Transistores.IntLib
|
|-- 02_Projetos_Fonte/                      <- Projetos de compilacao (.LibPkg) por categoria
|   |-- Modulos/Modulos.LibPkg
|   |-- CIs/CIs.LibPkg
|   |-- Conectores/Conectores.LibPkg
|   `-- ...
|
|-- 03_Modelos_3D/                          <- Arquivos de modelos 3D (.STEP) referenciados pelos footprints
|
|-- 04_Componentes_Para_Organizar/          <- Componentes avulsos encontrados pelo sistema para categorizar
|   |-- TMC2209/                            <- Driver de motor de passo TMC2209
|   |-- RPi_Pico/                           <- Modulo Raspberry Pi Pico
|   |-- HiLink/                             <- Fontes AC/DC Hi-Link
|   |-- MP1584/                             <- Step-Down DC-DC MP1584
|   |-- Displays_NHD/                       <- Displays LCD Newhaven
|   |-- PCB_Maria_Avulsos/                  <- Modulos e sensores avulsos (ESP32 DevKit, OLED, RFID, etc.)
|   |-- Cabecote_Duplo/                     <- Componentes do cabecote
|   `-- Outros_Avulsos/                     <- Reles e componentes avulsos (ex: DSY2Y, 20M05)
|
|-- 05_Bibliotecas_Gerais_Para_Destrinchar/ <- Bibliotecas volumosas que serao decompostas
|   |-- Biblioteca_Geral.IntLib             <- Biblioteca geral historica
|   |-- GPDSE.IntLib                        <- Compilada GPDSE (~93 MB)
|   `-- GPDSE_Fonte/                        <- 36 arquivos fonte (.SchLib e .PcbLib) separados do GPDSE
|
|-- Esquematicos/                           <- Esquematicos fonte (.SchLib) categorizados
|-- Footprints/                             <- Footprints fonte (.PcbLib) categorizados
`-- Historico de Atualizacao.txt            <- Registro de modificacoes
```
---

## Como incorporar novos componentes (Passo a Passo)

1. Abra o Altium Designer.
2. Abra o arquivo do componente avulso (ex: D:\Altium_Libraries_Master\04_Componentes_Para_Organizar\TMC2209\TMC2209_SILENTSTEPSTICK.SchLib).
3. Abra a biblioteca alvo oficial de esquematicos (ex: D:\Altium_Libraries_Master\Esquematicos\Modulos.SchLib).
4. No painel SCH Library, selecione o componente, copie (Ctrl+C) e cole (Ctrl+V) dentro de Modulos.SchLib.
5. Repita o mesmo procedimento para o Footprint: abra o .PcbLib avulso e o D:\Altium_Libraries_Master\Footprints\Modulos.PcbLib, colando o footprint correspondente.
6. Salve ambos os arquivos.
7. Abra o projeto de compilacao da categoria:
   D:\Altium_Libraries_Master\02_Projetos_Fonte\Modulos\Modulos.LibPkg
8. Clique com o botao direito no projeto no painel Projects e selecione Compile Integrated Library Modulos.LibPkg.
9. A nova versao de Modulos.IntLib sera gerada automaticamente e atualizada em 01_Bibliotecas_Integradas/.

---

## Como destrinchar as Bibliotecas Gerais (05_Bibliotecas_Gerais_Para_Destrinchar)

1. No Altium, de um File > Open e selecione o arquivo Biblioteca_Geral.IntLib.
2. O Altium perguntara: "Extract Sources" ou "Install Library".
3. Escolha "Extract Sources".
4. O Altium criara um projeto temporario com a lista de todos os esquematicos e footprints que estavam empacotados nela.
5. Agora voce pode navegar pelos componentes e mover os esquematicos/footprints para as bibliotecas certas (Resistores, CIs, Conectores, etc.).
