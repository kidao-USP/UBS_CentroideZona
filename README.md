# Otimização de Rota: Top 5 UBS por Centroide Urbano

## 📌 Sobre o Projeto
Este repositório contém o pipeline de dados geolocalizados para identificar as 5 Unidades Básicas de Saúde (UBS) mais acessíveis a pé a partir de cada centroide de zona urbana. 

## ⚙️ Arquitetura de Dados e Fluxo de Trabalho
Para otimizar o custo computacional do cálculo de rotas em malha viária real, o projeto utiliza uma abordagem de funil em duas etapas:

1. **Dados Base (Linha Reta):**
   - Extração das coordenadas originais (`.Rdata`).
   - Cálculo de matriz de distância em linha reta (Haversine, considerando a curvatura da Terra).
   - Armazenamento otimizado em formato `.parquet`.

2. **Pré-Filtro (K-Nearest Neighbors):**
   - Geração de uma base reduzida (`filtrado_top10_LR.parquet`) contendo estritamente as 10 UBS mais próximas em linha reta para cada centroide.

3. **Roteamento Real a Pé (OSRM):**
   - Levantamento da malha viária e restrições de pedestres utilizando um container do Open Source Routing Machine (OSRM).
   - Cálculo de distância e tempo de deslocamento a pé (walking profile) apenas para os pares pré-filtrados na etapa anterior.

4. **Resultado Final:**
   - Ranqueamento e extração das Top 5 UBS baseadas na distância real de caminhada computada pelo OSRM.

## 🛠️ Stack Tecnológico
- **Manipulação de Dados:** Formato `.parquet` para alta performance de I/O.
- **Motor de Roteamento:** OSRM (via Docker Container) com perfil de pedestre (`foot`).
- **Ambiente de Desenvolvimento:** Antigravity IDE (VS Code OSS) em servidor remoto.
- **Controle de Versão:** Git / GitHub.

## 🚀 Como Executar (Em construção)
Instruções futuras sobre como subir o container do OSRM e executar os scripts de extração...
