# Atividade 2 de Computação Gráfica - 2024.3 - Prof Celso Setsuo Kurashima

# Discentes
- Ana Carolina da Silva Martins
- Karl Eloy Henrique
- Francisco Yury Pinheiro Silva

## Vídeo de demonstração

Para ver o jogo funcionando, [clique aqui](https://drive.google.com/file/d/1OGZeqfUua4DHcL3dYxXEdSG1qNi08lK4/view?usp=drive_link).

## Arquivos
Consulte a pasta "Olha_o_sapo" deste repositório para obter os arquivos do projeto.
O programa é baseado nos seguintes arquivos:

**main.cpp**\
Este arquivo contém o ponto de entrada principal do aplicativo de visualização de modelos 3D. Cria uma instância da classe `abcg::Application`, que gerencia o ciclo de vida da aplicação OpenGL. Cria uma instância da classe Window, que define o comportamento da janela e a renderização dos modelos 3D. Define as configurações de OpenGL, como a quantidade de multisampling (samples = 4), que melhora a qualidade visual do modelo e as configurações da janela. Inicia o loop principal da aplicação, que gerencia a renderização, interação com o usuário e eventos da janela. Em caso de erro durante a execução, a aplicação captura exceções do tipo `std::exception` e imprime a mensagem de erro no terminal.

**model.cpp**\
Contém a implementação das principais funcionalidades relacionadas ao carregamento, manipulação e renderização de modelos 3D no aplicativo. Cria os buffers necessários para armazenar os dados do modelo na GPU: Vertex Buffer Object (VBO) e Element Buffer Object (EBO). Carrega um modelo 3D no formato .obj a partir do caminho fornecido com `loadObj(std::string_view path, bool standardize)`. Utiliza a biblioteca `tinyobj::ObjReader` para ler o arquivo. Armazena os vértices únicos e cria uma lista de índices para eliminar duplicação de vértices. Se a opção standardize for verdadeira, centraliza o modelo na origem e normaliza o tamanho para se ajustar ao espaço [-1, 1]. Renderiza o modelo 3D usando OpenGL com `render(int numTriangles) const`; determina o número de triângulos a serem desenhados e executa o comando `glDrawElements` para renderizar os triângulos armazenados no EBO. Configura o Vertex Array Object (VAO), que define como os vértices são processados: inicializa a posição e rotação do modelo, habilita o buffer de profundidade (depth buffering), necessário para a renderização 3D, vincula os atributos dos vértices (posição) ao VAO e configura a matriz de transformação do modelo e as variáveis uniformes relacionadas à projeção, cor e visualização. Desenha o modelo 3D na tela com `paint(glm::ivec2 m_viewportSize, GLuint program)`. Limpa o buffer de cor e o buffer de profundidade. Configura a matriz de transformação do modelo com translação, rotação e escala.

**model.hpp**\
Define a estrutura de dados e as funções para carregar, manipular e renderizar modelos 3D no aplicativo. Ele encapsula o gerenciamento de vértices, índices e buffers OpenGL necessários para a renderização eficiente dos objetos. A estrutura **Vertex** `glm::vec3 position:` define a posição 3D de um vértice no espaço. Carrega um arquivo de modelo 3D no formato .obj com `void loadObj(std::string_view path, bool standardize = true)`. Opcionalmente, o modelo pode ser padronizado para centralizar e normalizar suas dimensões. `void update(float red, float green, float blue)` atualiza os valores RGB para modificar dinamicamente a cor do modelo. Realiza a pintura do modelo no contexto OpenGL, configurando a matriz de modelo e aplicando transformações com `void paint(glm::ivec2 m_viewportSize, GLuint program)`. 

**trackball.cpp**\
 Implementa a classe TrackBall, que gerencia a interação de um trackball virtual para a manipulação de objetos 3D através de movimentos do mouse. Atualiza a rotação do trackball com base na posição atual do mouse com `void mouseMove(glm::ivec2 const &position)`. `project(position):` projeta a posição do mouse em coordenadas normalizadas (NDC) e ajusta para uma esfera virtual. Calcula o eixo de rotação com o produto vetorial entre a posição anterior e a atual. Ajusta a velocidade angular (m_velocity) e a aplica à rotação do objeto e concatena a nova rotação à rotação existente.

