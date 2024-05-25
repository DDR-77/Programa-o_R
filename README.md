# Programacao_R

getwd()# ver meu diretório de trabalho

# Estrutura de dados ------------------------------------------------------

#nome de um objeto:

a = 2
b <- 3

# Para criar um objeto, escolha um nome e use <- ou = para guardar a informação dentro do objeto


## operadores --------------------------------------------------------------
x == y # igual a
x != y # diferente de
x < y  # menor que
x > y  # maior que
x <= y # menor ou igual que
x >= y # maior ou igual que

soma <- a + b # adição
print(soma)

subtracao <- a - b # subtração
print(subtracao)

multiplicacao <- a * b # Multiplicação
print(multiplicacao)

divisao <- a / b # divisão
print(divisao)

modulo <- a %% b # resto da divisão
print(modulo)

potencia <- a ^ b # potência
print(potencia)


# Vetores -----------------------------------------------------------------

# - Um vetor é uma estrutura de dados unidimensional que pode conter ou não elementos de um único tipo
# - Os vetores podem ser subdivididos em : vetores atômicos e listas

## vetores atõmicos --------------------------------------------------------

# para criar um vetor use a função ""c()" (combine).
# para saber o tipo do vetor, use a função "typeof()".
# para saber seu comprimento use a função "length()".
# Você pode testar o determinado tipo de um vetor com a função "is*()".

### lógico ------------------------------------------------------------------
vet1 <- c(TRUE, FALSE)# lógico
# OU...
vet2 <- c(T, F)

typeof(vet1)
typeof(vet2)

is.logical(vet2)
is.logical(vet1)


### double ------------------------------------------------------------------

vet3 <- c(1,2.5,4.5)# Forma decimal
vet4 <- c(1.23e4)# Forma científica

typeof(vet3)
is.double(vet4)
length(vet4)

# Ecistem três valores especiais exclusivos para double: Inf, -Inf, e NaN(Not a Number).
vet5 <- c(Inf, -Inf, NaN)
typeof(vet5)
is.double(vet5)


### inteiro -----------------------------------------------------------------

# - Inyeiros são escritos da mesma forma que os doubles, mas  devem ser seguidos da letra "L".

vet6 <- c(1L,2L,6L, 10L)# inteiro
typeof(vet6)
is.integer(vet6)


### caractere(string) -------------------------------------------------------

# - As string são colocadas entre "".
vet7 <- c("Akio", "Scott", "James")
vet8 <- c("dia", "mês", "ano")
typeof(vet7)
is.character(vet8)

vet7[2]
vet8[3]

###  null -------------------------------------------------------------------


# - Embora não seja um vetor, NULLestá intimamente relacionado aos vetores e geralmente desempenha a função de um vetor genérico de comprimento zero.

vetor_null <- c(NULL)
vetor_null
typeof(vetor_null)


### NA ----------------------------------------------------------------------

# - Em R, “NA” (Not Available) é usado para representar valores ausentes ou desconhecidos.
na <- c(3,4,5,NA,7)
2*na
is.na(na)

mean(na, na.rm=T)
na[is.na(na)] <- 0
na


### coerção -----------------------------------------------------------------

# - Para vetores atômicos, o tipo é uma propriedade de todo o vetor

# - Todos os elementos devem ser do mesmo tipo.

# - Quando você tenta combinar tipos diferentes, eles serão forçados em uma ordem fixa: caractere → double → inteiro → lógico.

y <- c(1L, "leonardo")
y
typeof(y)


## Listas ------------------------------------------------------------------

#As listas são um avanço em complexidade em relação aos vetores atômicos: cada elemento pode ser de qualquer tipo
# Você constrói listas com a função "list()"

l1 <- list(1:4, "Caderno", c(TRUE, FALSE, TRUE), c(2.3,4.5))
print(l1)

l1[[4]][2]
l1[[2]]
l1[[1]]
l1[[3]][3]

# Você pode testar uma lista com is.list() e forçar uma lista com "as.list()"

is.list(l1)

x <- c(3:9)
is.list(x)
as.list(x)

unlist(x)


# Matrizes ----------------------------------------------------------------

# - Uma matriz em R é uma estrutura bidimensional que pode armazenar dados de um único tipo.
# - Isso significa que todos os elementos de uma matriz devem ser do mesmo tipo, como números inteiros, double ou caracteres.
# - Você pode criar uma matriz usando a função "matrix()". Especifique os dados e o número de linhas e colunas.

vet_1 <- c(1,2)
vet_2 <- c(3,4)
matriz1 <- matrix(c(vet_1, vet_2), nrow = 2, ncol = 2)
matriz1

is.matrix(matriz1)

dim(matriz1)

ncol(matriz1)

# Os elementos de uma matriz podem ser acessados usando índices de linha e coluna.

matriz1[1,2]#Acessando o elemento na primeira linha e segunda coluna

# adicionando nomes

row.names(matriz1) = c("linha1", "linha2")
colnames(matriz1) <- c("coluna1", "coluna2")
matriz1

matriz1[,"coluna1"]


# Array -------------------------------------------------------------------

#Um array em R é uma estrutura de dados multidimensional que pode conter elementos de um único tipo. Diferentemente das matrizes, os arrays podem ter mais de duas dimensões.
#Você pode criar um array usando a função "array()". Especifique os dados e as dimensões.

vec1 <- c(1L,2L,3L,4L)
vec2 <- c(5L,6L,7L,8L)
vec3 <- c(5L,6L,7L,8L)
meu_array <- array(c(vec1,vec2), dim = c(2,2,3))
meu_array  
  
typeof(meu_array)

# os elementos de um array são acessados usando índices correspondentes às dimensões.

meu_array[1,2,2] #linas x colunas x camadas 
meu_array[,,1] # acessando a matriz da primeira camada
meu_array[,,2] # acessando a matriz da segunda camada


# Data Frame --------------------------------------------------------------

# - No R, um data frame é uma estrutura de dados bidimensional semelhante a uma tabela em um banco de dados relacional ou a uma planilha.
# - Cada coluna em um data frame pode conter dados de diferentes tipos, tornando-os especialmente úteis para representar conjuntos de dados complexos.
# Você pode criar um dada frame manualmente usando a função "data.frame()".

meu_data_frame <- data.frame(
  nome = c("Akio","Scott","James"),
  Idade = c(17,17,16),
  nota = c(85, 92, 78)
)
str(meu_data_frame)#informações sobre as colunas
meu_data_frame

dados_climaticos <- data.frame(
  dia = seq(from = as.Date("2023-01-01"), by = "days", length.out = 5),
  temperatura = c(25.3, 24.5, 22.0, 26.8, 23.5),
  umidade = c(65, 70,75, 60, 80),
  velocidade_vento = c(10,12,8,15,9))
print(dados_climaticos)

head(dados_climaticos, 5)# para visualizar a quantidade de colunas

# Você também pode acessar elementos por índice de linha e coluna.

dados_climaticos$temperatura
dados_climaticos$umidade
dados_climaticos$velocidade_vento

# Outra maneira de acessar as informações é usando a função "subset()".

subset(dados_climaticos,umidade>70)
subset(dados_climaticos,temperatura>21)


# Atributos ---------------------------------------------------------------

# - Além dos próprios elementos, os vetores podem ter atributos que fornecem informações adicionais sobre os dados.

## nomes -------------------------------------------------------------------

# Você pode atribuir nomes a cada elemento do vetor usando a função "names()". Isso facilita a referência a elementos específicos pelo nome.

meu_vetor <- c(1,2,3)
names(meu_vetor) <- c("primeiro","segundo","terceiro")
meu_vetor

attributes(meu_vetor)

# Formas alternativas para nomear um vetor

x1 <- c(a = 1, b = 2, c = 3)
x1

x2 <- setNames(1:3, c("a", "b","c"))
x2


## dimensão ----------------------------------------------------------------

# Em R, vetores podem ter atributos de dimensão, que são comumente associados a matrizes.

m_vetor <-1:5
m_vetor
dim(m_vetor)<- c(5,1)# lina x coluna
m_vetor

attributes(m_vetor)


## funções -----------------------------------------------------------------

# A classe de um objeto é uma propriedade que indica a natureza ou tipo do objeto em termos de programação orientada a objetos
# A classe é uma parte fundamental em R, pois determina como o objeto será tratado em operações específicas e quais métodos (funções associadas) podem ser aplicados a ele.

# - Aqui estão algumas das classes mais comuns em R:
  
#numeric: Números reais (double).
#integer: Números inteiros.
#logical: Valores lógicos (TRUE ou FALSE).
#character: Strings de caracteres.
#factor: Fatores, usados para representar variáveis categóricas com níveis
#Date: Representação de datas.
#POSIXct e POSIXlt: Representação de datas e horas.
#data.frame: Uma estrutura bidimensional que pode conter colunas de diferentes classes.
#matrix: Uma estrutura bidimensional que contém elementos de uma única classe.
#array: Uma estrutura de dados multidimensional que pode conter elementos de uma única classe.
#list: Uma estrutura que pode conter elementos de diferentes classes e até outras listas.
#function: Funções.

# Em R, a função "class()" é usada para obter a classe de um obejeto

vet1 = c(1,2)
vet2 = c(3,4)
class(vet1)
class(vet2)

matriz1 <- matrix(c(vet1, vet2), nrow = 2, ncol = 2)
matriz1

# Você pode atribuir uma classe a um vetor usando a função "class()". Isso é comumente usado em programação orientada a objeto em R.
vec <- c(1,2,3,4)
class(vec)

class(vec)<- "minha_classe"
class(vec)

# criando um obejto da classe pessoa.

human <- structure(
  c("Akio"),
  idade = 17,
  last_name = "Takahiro,",
  class = "pessoa"
)
human
class(human)
