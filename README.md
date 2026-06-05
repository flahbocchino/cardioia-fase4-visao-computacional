# CardioIA – Fase 4: Assistente Cardiológico Virtual com Visão Computacional

**Aluna:** Flávia Nunes Bocchino | **RM:** 564213  
**Curso:** FIAP — Inteligência Artificial  

> ⚠️ Sistema acadêmico. Não substitui avaliação médica profissional.

## Sobre
Protótipo de classificação de imagens de raio-X de tórax usando CNNs, como parte da evolução do CardioIA — sistema de apoio cardiológico inteligente.

## Dataset
Chest X-Ray Images (Pneumonia) — Kaggle  
Classes: NORMAL vs PNEUMONIA | 5.856 imagens

## Resultados
| Modelo | Acurácia |
|---|---|
| CNN do Zero | 81% |
| MobileNetV2 (Transfer Learning) | 90% |

## Como Executar
1. Abra o notebook em `notebooks/fase4_parte1_preprocessamento.ipynb`
2. Monte o Google Drive com o `chest_xray.zip`
3. Execute todas as células em sequência

## Repositórios Anteriores
- [Fase 1 — Tabagismo e Vape](https://github.com/flahbocchino/cardioia-fase1-tabagismo-vape)
- [Fase 3 — Monitoramento Contínuo](https://github.com/flahbocchino/cardioia-fase3-iot-monitoramento_flaviabocchino)
