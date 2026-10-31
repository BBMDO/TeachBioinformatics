
# TeachBioinformatics | BTC220 – UFABC

## Sítios de Interação, Docking Molecular e Dinâmica Molecular
### Estudo de caso: Reposicionamento de fármacos em processos inflamatórios

Este repositório contém o roteiro de uma atividade prática de Bioinformática Estrutural desenvolvida para a disciplina **BTC220 – UFABC**, com foco na identificação de sítios de interação, docking molecular e avaliação *in silico* de propriedades farmacocinéticas e toxicológicas de compostos com potencial anti-inflamatório.

A atividade utiliza a estrutura cristalográfica da **interleucina-1 beta humana (IL-1β)** como modelo para explorar estratégias computacionais de reposicionamento de fármacos (*drug repurposing*).

---

## Responsáveis

- **Prof. Danilo T. Amaral**
- **MsC. João A. Teodoro**

**E-mails:**
- danilo.trabuco@ufabc.edu.br
- joao.teodoro@ufabc.edu.br

---

## Objetivos da atividade

Ao final da atividade, espera-se que os estudantes sejam capazes de:

- Consultar bancos de dados de estruturas tridimensionais de proteínas.
- Visualizar e interpretar estruturas proteicas e seus ligantes.
- Identificar possíveis sítios de ligação utilizando ferramentas de predição de cavidades.
- Investigar regiões de interação por meio de mapeamento de fragmentos.
- Consultar bancos de dados de compostos bioativos e medicamentos.
- Realizar docking molecular entre proteínas e pequenos ligantes.
- Interpretar poses de ligação, resíduos de interação e pontuações de docking.
- Avaliar propriedades farmacocinéticas e toxicológicas por ferramentas de ADMET.
- Integrar resultados computacionais para selecionar potenciais candidatos a fármacos.

---

## Estudo de caso: IL-1β humana

| Parâmetro | Informação |
|---|---|
| Proteína-alvo | Interleucina-1 beta humana (IL-1β) |
| PDB ID | [8C3U](https://www.rcsb.org/structure/8C3U) |
| Organismo | *Homo sapiens* |
| Sequência | 153 aminoácidos |
| Ligante cristalográfico | T9C |
| Aplicação | Reposicionamento de fármacos anti-inflamatórios |

**Sequência de aminoácidos:**

```text
APVRSLNCTLRDSQQKSLVMSGPYELKALHLQGQDMEQQVVFSMSFVQGEESNDKIPVALGLKEKNLYLSCLKDDKPTLQLESVDPKNYPKKKMEKRFVFNKIEINNKLEFESAQFPNWYISTSQAENMPVFLGGTKGGQDITDFTMQFVS
```

**Ligante cristalográfico (T9C):**

(S)-4'-hydroxy-3'-(6-methyl-2-oxo-3-(1H-pyrazol-4-yl)indolin-3-yl)-[1,1'-biphenyl]-2,4-dicarboxylic acid

O ligante T9C será utilizado como referência estrutural para comparar as regiões de interação identificadas nas análises de docking.

---

# Roteiro da atividade

## Aula 1 – Análise estrutural e identificação de sítios de interação

### Parte I – PDB e análise estrutural da proteína

**Objetivo:** Obter, visualizar e compreender a estrutura tridimensional da proteína-alvo.

**Ferramentas:**

- [RCSB Protein Data Bank](https://www.rcsb.org/)
- [Mol* Viewer](https://molstar.org/viewer/)
- [PlayMolecule](https://open.playmolecule.org/)

**Procedimento:**

1. Acesse o [RCSB PDB](https://www.rcsb.org/).
2. Pesquise pelo código **8C3U**.
3. Consulte as informações estruturais da proteína, incluindo organismo, sistema de expressão, sequência de aminoácidos, massa molecular e resolução estrutural.
4. Clique em **Download Files** e selecione **Legacy PDB Format**.
5. Abra o arquivo no Mol* Viewer ou PlayMolecule para visualizar a estrutura tridimensional.
6. Utilize os arquivos disponibilizados neste repositório:
   - `8C3U-protein.pdb`
   - `8C3U-ligand.pdb`
7. Faça o upload dos arquivos e explore a estrutura da proteína e do ligante.
8. Clique sobre diferentes regiões da estrutura para identificar resíduos de aminoácidos e átomos.

**Observação:** A estrutura cristalográfica original apresenta duas cadeias proteicas (A e B) e um ligante. Para esta atividade, serão utilizados os arquivos preparados e disponibilizados no repositório.

### Parte II – Identificação de regiões e sítios de ligação

**Objetivo:** Identificar possíveis cavidades e regiões de interação na proteína-alvo utilizando diferentes abordagens computacionais.

#### 1. Predição de cavidades com FpocketWeb

**Ferramenta:** [FpocketWeb](https://durrantlab.pitt.edu/fpocketweb/)

1. Faça o upload do arquivo `8C3U-protein.pdb`.
2. Clique em **Start FpocketWeb**.
3. Aguarde o processamento da estrutura.
4. Analise os pockets identificados e os respectivos parâmetros:
   - Score;
   - Druggability.
5. Selecione os pockets de maior interesse, considerando conjuntamente os parâmetros e sua localização na estrutura.
6. Faça o download dos resultados.
7. Extraia os arquivos e organize os seguintes dados em uma pasta:
   - `8C3U-protein_out.pdb`;
   - `pocket1_atm.pdb`;
   - `pocket2_atm.pdb`.
8. Abra os arquivos no Mol* Viewer para visualizar as cavidades identificadas.
9. Compare a localização do ligante cristalográfico T9C com os pockets preditos.

**Nota:** No estudo de caso, os pockets #1 e #2 foram selecionados para comparação com os resultados do FTMap. Score e Druggability são indicadores computacionais e não devem ser utilizados isoladamente para determinar a relevância de uma cavidade.

#### 2. Mapeamento de regiões de interação com FTMap

**Ferramenta:** [FTMap](https://ftmap.bu.edu/login.php)

1. Acesse a plataforma.
2. Selecione **Use FTMap without your own account**.
3. Defina um nome para a análise em **Job Name**.
4. Faça o upload de `8C3U-protein.pdb`.
5. Selecione a cadeia **A**.
6. Clique em **Map**.
7. Acompanhe o processamento e consulte os resultados pelo ID da análise.

**Observação:** Como o processamento pode demorar, o arquivo `8C3U-ftmap.pdb` disponibilizado no repositório poderá ser utilizado durante a aula.

Analise os resultados considerando os resíduos com maior afinidade de interação, dando atenção especial às maiores porcentagens de ocupação e aos valores superiores a 10%.

#### 3. Identificação de sítios por FINDSITEcomb2

**Ferramenta:** [FINDSITEcomb2](https://sites.gatech.edu/cssb/FINDSITE-COMB-2/)

1. Acesse a plataforma.
2. Selecione **For virtual ligand screening**.
3. Preencha os campos:
   - Sequence name;
   - Email address for returning results;
   - Re-enter email.
4. Faça o upload do arquivo da proteína preparada.
5. Mantenha a opção **6507 DrugBank drugs**.
6. Clique em **Send**.
7. Consulte os resultados enviados por e-mail.

#### 4. Integração dos resultados

Compare os sítios identificados pelo FpocketWeb, FTMap e FINDSITEcomb2.

Considere:

- A localização das cavidades na estrutura proteica;
- A proximidade com o ligante cristalográfico T9C;
- A concordância entre as diferentes ferramentas;
- A relevância dos resíduos envolvidos nas regiões identificadas.

---

## Aula 2 – Docking molecular e avaliação ADMET

### Parte III – Bancos de dados de compostos e docking molecular

**Objetivo:** Investigar compostos conhecidos e avaliar suas possíveis interações com a proteína IL-1β.

#### 1. Exploração de bancos de dados

**Ferramentas:**

- [ZINC Database](https://zinc.docking.org/substances/home)
- [DrugBank](https://go.drugbank.com/drugs)

Explore os bancos de dados e suas possibilidades de busca e filtragem por:

- Massa molecular;
- Aprovação regulatória;
- Classificação dos compostos;
- Disponibilidade comercial;
- Propriedades químicas.

#### 2. Busca por compostos estruturalmente semelhantes

Utilize a seguinte sequência SMILES para realizar a busca de compostos semelhantes:

```text
Cc1ccc2c(c1)NC(=O)C2(c3cc(ccc3O)c4ccc(cc4C(=O)O)C(=O)O)c5c[nH]nc5
```

Analise os resultados e identifique compostos semelhantes, observando as classificações disponíveis, como **Approved**.

Os seguintes compostos serão utilizados como candidatos para as análises:

| Composto | Classe / aplicação |
|---|---|
| Ibuprofeno | Anti-inflamatório não esteroidal |
| Prednisolona | Corticosteroide |
| Acetilcarnitina | Derivado da carnitina |
| Padimate O | Filtro UV |

Faça o download dos compostos disponibilizados em formatos `.sdf` e `.smiles` e organize-os na pasta `Substrates`.

#### 3. Docking molecular com CB-Dock2

**Ferramenta:** [CB-Dock2](https://cadd.labshare.cn/cb-dock2/index.php)

Como alternativa, também é possível utilizar o [HADDOCK 2.4](https://rascar.science.uu.nl/haddock2.4/), mediante cadastro. Entretanto, o processamento pode levar algumas horas.

**Procedimento:**

1. Acesse o CB-Dock2.
2. Selecione a opção **DOCK**.
3. Faça o upload do arquivo da proteína-alvo em formato `.pdb`.
4. Faça o upload do primeiro ligante em formato `.sdf`.
5. Selecione **Search Cavities**.
6. Em seguida, selecione **Auto Dock Blind**.
7. Submeta a análise e aguarde o processamento.
8. Clique em **View Results** para visualizar os resultados.

Repita o procedimento para os quatro compostos:

- Ibuprofeno;
- Prednisolona;
- Acetilcarnitina;
- Padimate O.

#### 4. Análise dos resultados de docking

Para cada composto, avalie:

- CurPocket ID;
- Pontuação de docking (Vina score);
- Resíduos envolvidos na interação;
- Interações intermoleculares;
- Localização do ligante na proteína.

Utilize a opção **Contact View** para visualizar os resíduos de interação.

Faça o download das poses de docking em formato PDB (complexos proteína-ligante).

#### 5. Comparação estrutural com o ligante cristalográfico

**Ferramenta:** [Mol* Viewer](https://molstar.org/viewer/)

Utilize o arquivo `vina_dock-T9C.pdb`, disponibilizado pelo professor, como referência estrutural.

1. Abra o complexo de referência contendo o ligante T9C.
2. Abra os complexos obtidos no CB-Dock2.
3. Compare visualmente as posições dos ligantes.
4. Identifique quais compostos apresentam poses próximas à posição experimental do T9C.
5. Verifique se os compostos ocupam a mesma região de interação ou cavidade.

**Critério de seleção:** Considere conjuntamente a pontuação de docking (valores mais negativos), a localização do ligante e sua proximidade espacial com a pose cristalográfica do T9C.

A pontuação de docking não deve ser utilizada isoladamente como evidência de afinidade ou atividade biológica.

### Parte IV – Predição de toxicidade e propriedades farmacocinéticas

**Objetivo:** Avaliar as propriedades ADMET (*Absorption, Distribution, Metabolism, Excretion and Toxicity*) dos compostos selecionados.

#### 1. Análise com ADMETlab 3.0

**Ferramenta:** [ADMETlab 3.0](https://admetlab3.scbdd.com/server/screening)

1. Acesse a plataforma.
2. Adicione os arquivos `.sdf` dos compostos selecionados.
3. Clique em **Submit**.
4. Após o processamento, clique em **View**.
5. Analise os parâmetros relacionados à toxicidade, absorção, distribuição, metabolismo e excreção.

#### 2. Análise com pkCSM

**Ferramenta:** [pkCSM](https://biosig.lab.uq.edu.au/pkcsm)

1. Acesse a plataforma.
2. Selecione **pkCSM**.
3. Insira os arquivos ou sequências SMILES dos compostos selecionados.
4. Clique em **ADMET**.
5. Analise os resultados preditivos.

#### 3. Integração e seleção do candidato

Reúna os resultados das análises estruturais, docking molecular e predição ADMET.

Considere os seguintes critérios para selecionar o composto mais promissor:

- Pontuação de docking;
- Compatibilidade espacial com a região de ligação do T9C;
- Resíduos e interações intermoleculares;
- Propriedades farmacocinéticas;
- Potencial toxicidade.

Ao final, selecione o composto com o perfil computacional mais favorável e justifique sua escolha com base nos resultados obtidos.

---

## Ferramentas e recursos

| Ferramenta | Aplicação |
|---|---|
| [RCSB PDB](https://www.rcsb.org/) | Banco de dados de estruturas proteicas |
| [Mol* Viewer](https://molstar.org/viewer/) | Visualização molecular |
| [PlayMolecule](https://open.playmolecule.org/) | Visualização e análise estrutural |
| [FpocketWeb](https://durrantlab.pitt.edu/fpocketweb/) | Identificação de cavidades |
| [FTMap](https://ftmap.bu.edu/login.php) | Mapeamento de regiões de interação |
| [FINDSITEcomb2](https://sites.gatech.edu/cssb/FINDSITE-COMB-2/) | Predição de sítios e triagem virtual |
| [ZINC](https://zinc.docking.org/substances/home) | Banco de dados de compostos |
| [DrugBank](https://go.drugbank.com/drugs) | Banco de dados de medicamentos |
| [CB-Dock2](https://cadd.labshare.cn/cb-dock2/index.php) | Docking molecular |
| [HADDOCK 2.4](https://rascar.science.uu.nl/haddock2.4/) | Docking molecular |
| [ADMETlab 3.0](https://admetlab3.scbdd.com/server/screening) | Predição de propriedades ADMET |
| [pkCSM](https://biosig.lab.uq.edu.au/pkcsm) | Predição farmacocinética e toxicidade |

**Conversor de formatos moleculares:** [ChemInfo Format Converter](https://www.cheminfo.org/Chemistry/Cheminformatics/FormatConverter/index.html)

---

## Considerações importantes

- Os resultados das ferramentas podem variar conforme suas versões, parâmetros e atualizações dos bancos de dados.
- As análises realizadas são preditivas e *in silico*, não substituindo experimentos bioquímicos, farmacológicos ou toxicológicos.
- Pontuações de docking não representam diretamente valores experimentais de afinidade de ligação.
- A concordância entre diferentes ferramentas pode fortalecer uma hipótese, mas não comprova a existência de uma interação biologicamente relevante.
- A seleção final deve considerar a integração de diferentes evidências computacionais.

---

## Resultado esperado

Ao término da atividade, os estudantes deverão apresentar uma análise comparativa dos quatro compostos investigados, integrando os resultados de identificação de cavidades, docking molecular e predição ADMET.

O objetivo final é propor um candidato com perfil computacional promissor para investigação de possíveis interações com a IL-1β humana, dentro da perspectiva de reposicionamento de fármacos.

---

**TeachBioinformatics | UFABC**

*Bioinformatics education through practical computational approaches.*
