Crisp dm
- Entendimento do negócio: Definir e compreender o contexto e o problema a ser resolvido.
- Entendimento dos dados: Coletar, analisar e compreender os dados disponíveis.
- Preparação dos dados: Limpar, transformar, integrar e formatar os dados.
- Modelagem: Aplicar técnicas de mineração e ajustar parâmetros.
- Verificação: Confirmar se o modelo atende aos objetivos do negócio.
- Implantação: Colocar o modelo em produção ou entregue aos tomadores de decisão.
Essas etapas são iterativas, permitindo que as equipes retorne a etapas anteriores para ajustes 
conforme novos insights surgem. O CRISP-DM é flexível e genérico, aplicável a qualquer tipo de 
problema de análise de dados.


- Accuracy evaluates overall correctness but can be misleading for imbalanced datasets.


- Precision emphasizes the reliability of positive predictions, minimizing false positives.


- Recall focuses on capturing all actual positives, minimizing false negatives.


temos 1000 dados
2 funçoes(aprovar bons pagadores e recusar mals)

rede chegou com acuracia de 98%
dos 1000, 980 são bons, e 20 ruins


acuracia leva em consideração quantos acertos("de todos os cados que eu tinha, acertei 90%")
precisão depende do que se procura
f1-score é a média entre a acuracia e a precisão


curva galseana(68,36 - 95,5 - 99,7)
desvio padrao
expllicaçaõ do codigo(loc = media, scale = desvio padrao, lam = valor esperado/normal/mais comum, )

indeterminada


como criar os diferentes tipos de grafico

como executar filtragens

conceitos de acuracia, precisão, recall e f1-score