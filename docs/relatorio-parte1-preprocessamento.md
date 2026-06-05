# Relatório — Parte 1: Pré-processamento de Imagens Médicas

**Projeto:** CardioIA – Fase 4  
**Aluna:** Flávia Nunes Bocchino | **RM:** 564213  
**Disciplina:** Inteligência Artificial e Visão Computacional — FIAP  

---

## 1. Dataset Selecionado

**Nome:** Chest X-Ray Images (Pneumonia) — Kaggle (Paul Mooney)  
**Link:** https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia  
**Classes:** NORMAL e PNEUMONIA  
**Total:** 5.856 imagens  

**Justificativa:** Dataset público, binário, amplamente usado academicamente e diretamente relacionado ao contexto do CardioIA. Raio-X de tórax já estava presente na Fase 1 do projeto.

---

## 2. Pipeline de Pré-processamento

| Etapa | Decisão | Justificativa |
|---|---|---|
| Redimensionamento | 150x150 px | Equilibra qualidade e memória no Colab gratuito |
| Normalização | Pixels ÷ 255 | Escala [0,1] estabiliza o treinamento |
| Data Augmentation | Rotação, zoom, flip | Reduz overfitting no treino |
| Desbalanceamento | class_weight proporcional | PNEUMONIA tem 3x mais imagens que NORMAL |

### Divisão dos conjuntos

| Conjunto | NORMAL | PNEUMONIA | Total |
|---|---|---|---|
| Treino | 1.341 | 3.875 | 5.216 |
| Validação | 8 | 8 | 16 |
| Teste | 234 | 390 | 624 |

---

## 3. Limitações Identificadas

- Conjunto de validação muito pequeno (16 imagens), limitando a confiabilidade das métricas durante o treino.
- Dataset desbalanceado — mitigado com class_weight, discutido no relatório de ética.
- Imagens predominantemente pediátricas, o que pode limitar generalização para adultos.

---

## 4. Ferramentas

Python 3 · TensorFlow/Keras · ImageDataGenerator · Matplotlib · Google Colab
