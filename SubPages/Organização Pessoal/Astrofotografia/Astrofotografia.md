---

---
Curso do Observatório Valongo UFRJ

Campo de visão (FoV)

Depende da distância focal da lente (variável conforme a lente) e do tamanho do sensor da câmera (Fixo)

[https://wiki.openastrotech.com/OpenAstroTracker](https://wiki.openastrotech.com/OpenAstroTracker)

[Cálculo de tempo de exposição](http://web.archive.org/web/20200220123345/https://www.sahavre.fr/tutoriels/astrophoto/34-regle-npf-temps-de-pose-pour-eviter-le-file-d-etoiles)

[https://www.geogebra.org/?lang=pt](https://www.geogebra.org/?lang=pt)

[http://deepskystacker.free.fr/portuguese/index.html](http://deepskystacker.free.fr/portuguese/index.html)

[https://www.microsoft.com/store/apps/9nnj470dnd48](https://www.microsoft.com/store/apps/9nnj470dnd48)

Matriz de bayer
    Modificação de filtro p/ h-alfa
![[SubPages/Pessoal/images/Untitled 45.png]]
![[SubPages/Pessoal/images/Untitled 46.png]]
![[SubPages/Pessoal/images/Untitled 47.png]]
![[SubPages/Pessoal/images/Untitled 48.png]]
![[SubPages/Pessoal/images/Untitled 49.png]]
![[SubPages/Pessoal/images/Untitled 50.png]]
![[SubPages/Pessoal/images/Untitled 51.png]]
![[SubPages/Pessoal/images/Untitled 52.png]]
![[SubPages/Pessoal/images/Untitled 53.png]]
![[SubPages/Pessoal/images/Untitled 54.png]]
![[SubPages/Pessoal/images/Untitled 55.png]]
![[SubPages/Pessoal/images/Untitled 56.png]]
![[SubPages/Pessoal/images/Untitled 57.png]]
![[SubPages/Pessoal/images/Untitled 58.png]]
![[SubPages/Pessoal/images/Untitled 59.png]]
    Mapas de bias frames
        Tirado com tempo de exposição muito baixo e lente fechada.
        Pode-se fazer uma foto desta para cada faixa de ISO e manter o arquivo guardado para utilização.
        Melhor ainda se for com empilhamento para remover os ruidos aleatorios
![[Untitled.jpeg]]
![[SubPages/Pessoal/images/Untitled 60.png]]
![[SubPages/Pessoal/images/Untitled 61.png]]
![[SubPages/Pessoal/images/Untitled 62.png]]
![[SubPages/Pessoal/images/Untitled 63.png]]
![[SubPages/Pessoal/images/Untitled 64.png]]
![[SubPages/Pessoal/images/Untitled 65.png]]
![[Untitled 1.jpeg]]
![[SubPages/Pessoal/images/Untitled 66.png]]
![[SubPages/Pessoal/images/Untitled 67.png]]
![[SubPages/Pessoal/images/Untitled 68.png]]
![[SubPages/Pessoal/images/Untitled 69.png]]
![[SubPages/Pessoal/images/Untitled 70.png]]
![[SubPages/Pessoal/images/Untitled 71.png]]
![[SubPages/Pessoal/images/Untitled 72.png]]
![[SubPages/Pessoal/images/Untitled 73.png]]
![[SubPages/Pessoal/images/Untitled 74.png]]
![[SubPages/Pessoal/images/Untitled 75.png]]
![[SubPages/Pessoal/images/Untitled 76.png]]
![[SubPages/Pessoal/images/Untitled 77.png]]
![[SubPages/Pessoal/images/Untitled 78.png]]
![[SubPages/Pessoal/images/Untitled 79.png]]
![[SubPages/Pessoal/images/Untitled 80.png]]
![[SubPages/Pessoal/images/Untitled 81.png]]
![[SubPages/Pessoal/images/Untitled 82.png]]
![[SubPages/Pessoal/images/Untitled 83.png]]
![[SubPages/Pessoal/images/Untitled 84.png]]
![[SubPages/Pessoal/images/Untitled 85.png]]
![[SubPages/Pessoal/images/Untitled 86.png]]
![[SubPages/Pessoal/images/Untitled 87.png]]
![[SubPages/Pessoal/images/Untitled 88.png]]
![[SubPages/Pessoal/images/Untitled 89.png]]
    Virar para o ponto cardeal sul (bússola) e inclinar um ângulo equivalente a latitude de onde vc está (pode usar inclinômetro de celular)
![[SubPages/Pessoal/images/Untitled 90.png]]
![[SubPages/Pessoal/images/Untitled 91.png]]
![[SubPages/Pessoal/images/Untitled 92.png]]
![[SubPages/Pessoal/images/Untitled 93.png]]
![[SubPages/Pessoal/images/Untitled 94.png]]
![[SubPages/Pessoal/images/Untitled 95.png]]
![[SubPages/Pessoal/images/Untitled 96.png]]
![[SubPages/Pessoal/images/Untitled 97.png]]
![[SubPages/Pessoal/images/Untitled 98.png]]
![[SubPages/Pessoal/images/Untitled 99.png]]
![[SubPages/Pessoal/images/Untitled 100.png]]
![[SubPages/Pessoal/images/Untitled 101.png]]
![[SubPages/Pessoal/images/Untitled 102.png]]
![[SubPages/Pessoal/images/Untitled 103.png]]
    FireCapture
![[SubPages/Pessoal/images/Untitled 104.png]]
![[SubPages/Pessoal/images/Untitled 105.png]]
![[SubPages/Pessoal/images/Untitled 106.png]]
![[SubPages/Pessoal/images/Untitled 107.png]]
![[SubPages/Pessoal/images/Untitled 108.png]]

![[SubPages/Pessoal/images/Untitled 109.png]]

Processamento:

Star Trail → Sequator

DSO → Deep Sky stacker
    O DSS alinha as fotos a serem empilhadas pela detecção de estrelas
    Antes de salvar, buscar alinhar os picos de RGB juntos, mais ou menos no ponto de mudança de concavidade da curva de contraste

# Roteiro:

## Pré-processamento no DSS

1: Opção "Abra suas Fotos"
- Escolher as fotos (light frames)
2: Abrir os dark, flat, bias frames
3: Opção "Verificar tudo"
4: Opção "Registrar fotos que foram verificadas"
- Marcar somente "Auto detecção de pixels quentes"
- Em avançado, alterar o limiar de forma a detectar uma grande quantidade de estrelas
- Clicar em "Configurações recomendadas". O que for problemático, vai aparecer em vermelho. O que estiver em verde, está OK
- Em "Parâmetros de integração, verificar o que for necessário"
5: Clicar em OK e aguardar a coclusão dos master frames
6: Na lista, escolher a foto com maior pontuação, clicar com o botão direito e Marcar "Usar como referência"
7: Clicar em "Integrar ficheiros verificados"
- Ajustar os parâmetros
- Clicar OK
- O resultado final estará como "Autosave.tif"

## Pós processamento no GIMP

1: Ampliar o histograma
- Cores -> Níveis
- Escolher "Value" como canal, o que significa RGB
- Buscar adequar as pontas (preto e branco), se necessário adequar o meio
- Repetir várias vezes até obter um histograma alargado
- Cuidar para não "clipar", o que acarretará em perda de informação

2: Remover o background (se necessário, mas quase sempre vai ser)
- Copiar toda a imagem para uma nova
- Na nova imagem, remover todas as estrelas. Para isso:
- Utilizar o G'MIC-qt em filtros
- Utilizar o recurso Remove Hot pixels, que irá remover a maioria das estrelas.
- Para remover as maiores, utilizar o "Healing Brush" do GIMP
- Colar novamente na Imagem original. Ela ficará acima da última camada, mas ainda não aplicada. Alterar o Modo para "Diferença" e mexer na opacidade
- Usar a âncora para aplicar na última camada

3: Nesta etapa pode ser necessário mexer nos níveis novamente para obter mais contraste

4: Curvas
- Aplicar uma curva S a fim de trazer a tona os meio tons

5: Saturação
- Pode-se aplicar a imagem toda ou mascarar algumas áreas
- Em geral, aumentar a saturação e diminuir a luminosidade, porém pode trazer alguns ruídos e aberrações à tona
- Para mascarar:
- Duplicar o Layer
- Alterar a saturação em todo o layer para o valor desejado para a área
- Clicar com o botão direito no layer e Adicionar máscara
- Clicar com o botão direito no layer e Editar máscara e Exibir máscara
- Pintar a máscara de preto
- Clicar com o botão direito, desativar a opção exibir máscara
- Na área desejada, pintar de branco com o pincel.

6: Caso ache necessário, remover o Halo magenta das estrelas.
- Selecionar por cor
- Subtrair áreas não desejadas
- Alterar os levels e curvas para o seleção desejada

[[Enviando por email 1905.13189.pdf]]

[[Enviando por email 1905.13189.pdf]]