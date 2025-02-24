<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Diagrama Estilizado</title>

<div style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; line-height: 1.6; margin: 0; padding: 20px; background-color: #f5f5f5;">
    <div style="max-width: 1200px; margin: 0 auto; background-color: white; padding: 30px; border-radius: 10px; box-shadow: 0 2px 10px rgba(0,0,0,0.1);">
        <h1 style="color: #2c3e50; text-align: center; margin-bottom: 40px; font-size: 2.5em;">Diagrama em pt-br</h1>

```mermaid
  flowchart TD
      classDef modulo fill:#f9f,stroke:#333,stroke-width:2px,color:#000
      classDef submodulo fill:#bbf,stroke:#333,stroke-width:1px,color:#000
      classDef tecnologia fill:#dfd,stroke:#333,stroke-width:1px,color:#000
      subgraph Coleta["Coleta de Dados"]
          direction TB
          A1[Sensores IoT]:::tecnologia
          A2[Bancos Públicos]:::tecnologia
          A3[Simulações]:::tecnologia
      end
      subgraph PreProcessamento["Pré-processamento"]
          direction TB
          B1[Normalização]:::submodulo
          B2[Limpeza]:::submodulo
          B3[Interpolação]:::submodulo
      end
      subgraph Analise["Análise Exploratória"]
          direction TB
          C1[Visualização]:::submodulo
          C2[FFT]:::submodulo
          C3[Tendência/Sazonalidade]:::submodulo
      end
      subgraph Modelagem["Modelagem"]
          direction TB
          D1[Estatística]:::submodulo
          D2[Redes Neurais]:::submodulo
      end
      subgraph Avaliacao["Avaliação"]
          direction TB
          E1[Métricas]:::submodulo
          E2[Testes]:::submodulo
      end
      subgraph Interface["Interface"]
          direction TB
          F1[Dashboard]:::submodulo
          F2[Exportação]:::submodulo
      end
      Coleta --> PreProcessamento
      PreProcessamento --> Analise
      Analise --> Modelagem
      Modelagem --> Avaliacao
      Avaliacao --> Interface
      Avaliacao -.->|Feedback| PreProcessamento
      Avaliacao -.->|Feedback| Analise
      Avaliacao -.->|Feedback| Modelagem
      subgraph Aplicacoes["Aplicações Práticas"]
          direction TB
          G1[Climática]:::tecnologia
          G2[Sísmica]:::tecnologia
          G3[Elétrica]:::tecnologia
      end
      Interface --> Aplicacoes
      class Coleta,PreProcessamento,Analise,Modelagem,Avaliacao,Interface modulo
```

  <div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
  <h2>Explicação do Diagrama</h2>
  <ul>
        <li>As caixas rosadas representam os módulos principais do projeto</li>
        <li>As caixas azuis mostram os subprocessos dentro de cada módulo</li>
        <li>As caixas verdes indicam tecnologias e ferramentas utilizadas</li>
        <li>As linhas sólidas mostram o fluxo principal de dados</li>
        <li>As linhas pontilhadas representam loops de feedback</li>
  </ul>
      </div>
  </div>
      <div style="max-width: 1200px; margin: 0 auto; background-color: white; padding: 30px; border-radius: 10px; box-shadow: 0 2px 10px rgba(0,0,0,0.1);">
        <h1 style="color: #2c3e50; text-align: center; margin-bottom: 40px; font-size: 2.5em;">Diagram in us-en</h1>

```mermaid
  flowchart TD
      classDef modulo fill:#f9f,stroke:#333,stroke-width:2px,color:#000
      classDef submodulo fill:#bbf,stroke:#333,stroke-width:1px,color:#000
      classDef tecnologia fill:#dfd,stroke:#333,stroke-width:1px,color:#000
      subgraph DataCollection["Data Collection"]
          direction TB
          A1[IoT Sensors]:::tecnologia
          A2[Public Databases]:::tecnologia
          A3[Mathematical Simulations]:::tecnologia
      end
      subgraph PreProcessing["Data Preprocessing"]
          direction TB
          B1[Normalization]:::submodulo
          B2[Data Cleaning]:::submodulo
          B3[Interpolation]:::submodulo
      end
      subgraph Analysis["Exploratory Analysis"]
          direction TB
          C1[Visualization]:::submodulo
          C2[FFT Analysis]:::submodulo
          C3[Trend/Seasonality]:::submodulo
      end
      subgraph Modeling["Modeling"]
          direction TB
          D1[Statistical Models]:::submodulo
          D2[Neural Networks]:::submodulo
      end
      subgraph Evaluation["Evaluation"]
          direction TB
          E1[Metrics]:::submodulo
          E2[Test Cases]:::submodulo
      end
      subgraph Interface["Interface"]
          direction TB
          F1[Dashboard]:::submodulo
          F2[Export]:::submodulo
      end
      DataCollection --> PreProcessing
      PreProcessing --> Analysis
      Analysis --> Modeling
      Modeling --> Evaluation
      Evaluation --> Interface
      Evaluation -.->|Feedback| PreProcessing
      Evaluation -.->|Feedback| Analysis
      Evaluation -.->|Feedback| Modeling
      subgraph Applications["Practical Applications"]
          direction TB
          G1[Climatic]:::tecnologia
          G2[Seismic]:::tecnologia
          G3[Electrical]:::tecnologia
      end
      Interface --> Applications
      class DataCollection,PreProcessing,Analysis,Modeling,Evaluation,Interface modulo
```

  <div style="background-color: #f8f9fa; padding: 20px; border-radius: 8px; margin: 20px 0;">
              <h2>Explanation</h2>
            <ul>
                <li>Pink boxes represent the main modules of the project</li>
                <li>Blue boxes show subprocesses within each module</li>
                <li>Green boxes indicate technologies and tools used</li>
                <li>Solid lines show the primary data flow</li>
                <li>Dotted lines represent feedback loops</li>
            </ul>
  </div>
</div>
</div>
