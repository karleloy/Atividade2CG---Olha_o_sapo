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

**main.cpp**
<p align="justify"> Este arquivo contém o ponto de entrada principal do aplicativo de visualização de modelos 3D. Cria uma instância da classe **abcg::Application**, que gerencia o ciclo de vida da aplicação OpenGL. Cria uma instância da classe Window, que define o comportamento da janela e a renderização dos modelos 3D. Define as configurações de OpenGL, como a quantidade de multisampling (samples = 4), que melhora a qualidade visual do modelo e as configurações da janela. Inicia o loop principal da aplicação, que gerencia a renderização, interação com o usuário e eventos da janela. Em caso de erro durante a execução, a aplicação captura exceções do tipo std::exception e imprime a mensagem de erro no terminal. </p>

**model.cpp**
<p align="justify"> Contém a implementação das principais funcionalidades relacionadas ao carregamento, manipulação e renderização de modelos 3D no aplicativo. Cria os buffers necessários para armazenar os dados do modelo na GPU: Vertex Buffer Object (VBO) e Element Buffer Object (EBO). Carrega um modelo 3D no formato .obj a partir do caminho fornecido com `loadObj(std::string_view path, bool standardize)` </p>

model.hpp

