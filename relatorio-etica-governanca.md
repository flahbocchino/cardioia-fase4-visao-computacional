# Relatório — Ética e Governança em Visão Computacional

**Projeto:** CardioIA – Fase 4  
**Aluna:** Flávia Nunes Bocchino | **RM:** 564213  
**Disciplina:** Inteligência Artificial e Visão Computacional — FIAP  

---

## 1. Introdução

O uso de Visão Computacional em contextos médicos exige atenção redobrada às questões éticas e de governança. Este relatório analisa as limitações do dataset utilizado no CardioIA Fase 4, identifica possíveis vieses e propõe práticas de mitigação.

---

## 2. Limitações e Vieses Identificados

### 2.1 Desbalanceamento de classes
O conjunto de treino contém aproximadamente 3x mais imagens de PNEUMONIA do que NORMAL (3.875 vs 1.341). Sem correção, o modelo tenderia a classificar tudo como PNEUMONIA, prejudicando pacientes saudáveis com falsos positivos.

**Mitigação aplicada:** uso de `class_weight` proporcional durante o treinamento.

### 2.2 Representatividade populacional
As imagens do dataset são predominantemente pediátricas. Um modelo treinado nesse contexto pode não generalizar bem para adultos, idosos ou populações de diferentes etnias e comorbidades.

**Mitigação proposta:** em ambiente real, o dataset deveria ser ampliado com imagens de diferentes faixas etárias, sexos e origens geográficas.

### 2.3 Conjunto de validação reduzido
O conjunto de validação original contém apenas 16 imagens, o que torna as métricas de validação durante o treino pouco confiáveis estatisticamente.

**Mitigação proposta:** uso de validação cruzada (k-fold) em projetos futuros.

### 2.4 Ausência de diversidade de condições
O dataset é binário (NORMAL vs PNEUMONIA) e não contempla outras condições pulmonares e cardíacas relevantes, como derrame pleural, cardiomegalia ou edema pulmonar.

**Mitigação proposta:** expansão para datasets multilabel como o NIH Chest X-rays em versões futuras do CardioIA.

---

## 3. Métricas de Fairness

### 3.1 Análise por classe — CNN do Zero

| Classe | Precision | Recall | F1 |
|---|---|---|---|
| NORMAL | 0.91 | 0.54 | 0.68 |
| PNEUMONIA | 0.78 | 0.97 | 0.86 |

O recall baixo para NORMAL (0.54) indica que o modelo erra com frequência ao classificar pacientes saudáveis como doentes (falsos positivos). Em contexto clínico real, isso geraria exames desnecessários e ansiedade nos pacientes.

### 3.2 Análise por classe — MobileNetV2

| Classe | Precision | Recall | F1 |
|---|---|---|---|
| NORMAL | 0.90 | 0.81 | 0.85 |
| PNEUMONIA | 0.89 | 0.95 | 0.92 |

O MobileNetV2 apresentou desempenho mais equilibrado entre as classes, com recall de NORMAL subindo de 0.54 para 0.81 — redução significativa de falsos positivos.

---

## 4. Implicações Éticas

- **Autonomia médica:** o sistema não deve substituir o julgamento clínico. Todo resultado deve ser interpretado por um profissional de saúde.
- **Transparência:** o modelo deve informar sempre o grau de confiança da predição e suas limitações conhecidas.
- **Responsabilidade:** em caso de erro do modelo, a responsabilidade recai sobre o sistema de saúde e não sobre o paciente.
- **Privacidade:** imagens médicas são dados sensíveis e devem ser tratadas com anonimização e controle de acesso rigorosos.

---

## 5. Conclusão

O CardioIA Fase 4 demonstra que modelos de Visão Computacional podem apoiar a triagem de imagens médicas com acurácia relevante. Contudo, seu uso responsável exige consciência sobre as limitações do dataset, monitoramento contínuo de fairness e governança clara sobre o papel do sistema no fluxo clínico.

> ⚠️ Este sistema é um protótipo acadêmico. Não deve ser utilizado para diagnóstico médico real.
