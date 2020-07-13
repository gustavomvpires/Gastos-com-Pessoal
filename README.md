# Gastos-com-Pessoal
Repositório com todas programações e resultados das Projeções para Gastos com Pessoal das Administrações Públicas

O modelo de simulação utilizado nesse texto trabalha com três populações básicas:
A = população de servidores ativos;
I = população de servidores inativos; e
P = população de pensionistas, herdeiros de servidores ativos ou inativos já falecidos.
A cada ano t, tem-se, assim, populações AE(t), IE(t) e PE(t) compostas, respectivamente, pelos servidores ativos e inativos e pelos pensionistas do estado E no ano t. Parece natural, assim, denotar os quantitativos de servidores ativos e inativos e pensionistas do estado E no ano t por, respectivamente, n(AE(t)), n(IE(t)) e n(PE(t)).
Em sendo assim, é fácil perceber que os gastos com servidores ativos do estado E no ano t podem ser escritos como:
Equação 1: GSAE(t) = Σ𝑤𝑖∗13,3n(𝐴𝐸(t))𝑖=1
onde i varia de 1 até n(AE(t)) e 𝑤𝑖 é o salário (i.e. a “remuneração média”) mensal de cada servidor ativo i de E em t.
Analogamente, os gastos com servidores inativos do estado E no ano t podem ser escritos como:
Equação 2: GSIE(t) = Σ𝑏𝑗∗13n(𝐼𝐸(t)) 𝑗=1
onde j varia de 1 até n(IE(t)) e 𝑏𝑗 é o benefício previdenciário mensal de cada servidor inativo j do estado de E no período t.
Por fim, os gastos com pensionistas do estado E no ano t podem ser escritos como:
Equação 3: GPE(t) = Σ𝑏𝑝𝑘∗13n(𝑃𝐸(t)) 𝑘=1
onde k = 1 até n(PE(t)) e 𝑏𝑝𝑘 é o benefício de pensão mensal médio de cada pensionista de E em t.
O motivo pelo qual a remuneração mensal dos servidores ativos é multiplicada por 13,3 é o fato de que os ativos – mas não os inativos e pensionistas – têm direito a férias remuneradas, além do décimo terceiro salário recebido pelos membros de todas as populações.
Parece justo supor, também, que a cada ano as populações de ativos e inativos mudam de acordo com as seguintes equações:
Equação 4: AE(t) = AE(t-1) + CE(t) – NIE(t) – FAE(t)
onde
CE(t) = população dos servidores ativos de E contratados no ano t;
NIE(t) = população de “novos inativos”, i.e. dos servidores de E que se aposentaram em t; e, por fim,
FAE(t) = população de servidores ativos de E que faleceram em t.
Ou seja, os ativos em um dado estado/ano são aqueles que estavam ativos no estado no ano anterior, mais os que foram contratados no estado no ano corrente, menos os que se aposentaram e faleceram no estado no ano corrente.
Equação 5: IE(t) = IE(t-1) + NIE(t) – FIE(t)
onde
FIE(t) = população de servidores inativos que faleceram em t.
Ou seja, os inativos em um dado estado/ano são aqueles que estavam inativos no estado no ano anterior, mais os que se aposentaram no estado no ano corrente, menos os que inativos que faleceram no estado no ano corrente.
Equação 6: PE (t) = PE (t-1) + α1∗ FAE(t) + α2∗FIE (t) – FPE (t)
onde
FPE (t) = população de pensionistas de E que faleceram em t; e
α1 e α2 são, respectivamente, os percentuais de servidores ativos e inativos que, ao falecerem, instituem pensões.
Ou seja, os pensionistas em um dado estado/ano são aqueles que do ano anterior, mais os pensionistas que foram instituídos no ano corrente devido a óbitos de servidores ativos e inativos, menos os que pensionistas que faleceram no estado no ano corrente.
As equações 1-6 compõem a estrutura básica do modelo utilizado nesse texto – que se propõe simples, intuitivo e, cuja dinâmica populacional subjacente é passível de representação gráfica (ver gráfico 1).
Gráfico 1: Representação básica da dinâmica das populações do modelo
Aposentadorias
NIE(t)
Óbitos de ativos Óbitos de inativos
CE(t) α1∗ FAE(t) α2∗ FIE (t)
Contratações
Óbitos de pensionistas FPE(t)
Embora conceitualmente simples, o modelo requer grande esforço de implementação, por três motivos básicos. Primeiramente há que garantir que as populações de ativos, inativos e pensionistas de cada estado possam ser adequadamente identificadas em algum “ano base” de referência, tão recente quanto possível. Em segundo lugar, há que estimar os “fluxos chave” do modelo, quais sejam, (i) o fluxo de novas aposentadorias de servidores a cada ano em cada estado, isto é NIE(t); (ii) os óbitos de servidores ativos, inativos e pensionistas a cada ano em cada estado, isto é FAE(t), FIE(t) e FPE(t), respectivamente; (iii) o fluxo de novas pensões criadas todos os anos, dados no modelo pelos parâmetros α1 e α2. Por fim, é necessário, ainda, traçar cenários para as políticas de pessoal de cada estado, vale dizer, sobre (a) o fluxo de novas contratações a cada ano; (b) o salário real de entrada dessas pessoas; e (c) os ganhos salariais derivados da progressão funcional dos servidores ativos, mesmo na inexistência de variações reais nos salários de entrada.
De outro modo, basta que um desses pré-requisitos não seja atendido – i.e. que haja problemas graves com (i) a identificação das populações no período de referência; ou (ii) com a estimação dos fluxos chave do modelo; ou ainda (iii) com a identificação das políticas de pessoal de cada estado – para que os resultados das simulações possam ficar bastante longe dos resultados efetivos observados em cada estado/ano.
Cumpre, portanto, explicitar ao leitor as hipóteses precisas adotadas nesse texto sobre as variáveis supracitadas. Esse é o objetivo da próxima seção.
Antes de prosseguir, entretanto, cumpre notar que a principal utilidade da abordagem proposta nesse texto não é a capacidade preditiva strictu sensu, mas a construção de cenários prospectivos. Como apontado anteriormente, previsões precisas para os gastos com pessoal de cada estado a partir do modelo dessa seção requerem previsões precisas sobre um número relativamente grande de variáveis exógenas – sejam elas biométricas ou de política – e, portanto, são difíceis de alcançar. A força das conclusões desse texto não deriva, portanto, da suposição de que o modelo permite – ou que os autores da análise, de alguma maneira, possam – determinar com precisão ex-ante as trajetórias efetivas do gasto com pessoal nos estados brasileiros, por exemplo, na próxima década. Deriva, alternativamente, da constatação de que, dadas as condições iniciais discutidas na seção 4, os cenários qualitativos propostos nesse texto são robustos no espaço de variação plausível das variáveis exógenas (notadamente de política) do modelo.
