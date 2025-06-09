# Math Quest: Aventura Matemática 🌟

Bem-vindo ao Math Quest, um jogo interativo de quiz matemático projetado para desafiar suas habilidades e se divertir enquanto aprende! Responda a uma série de perguntas matemáticas, use dicas quando necessário e tente alcançar a maior pontuação possível.

## 🎮 Sobre o Jogo

Math Quest é um jogo baseado em turnos onde você responde a 10 perguntas de matemática selecionadas aleatoriamente de um banco de questões. Para cada pergunta, você tem três tentativas para acertar a resposta. A pontuação obtida por pergunta depende do número de tentativas restantes.

O jogo apresenta:
- Uma interface de usuário interativa criada com ipywidgets.
- Feedback visual para respostas corretas e incorretas.
- Um sistema de dicas para ajudar a resolver problemas mais desafiadores.
- Acompanhamento de pontuação e progresso em tempo real.
- Gráficos de progresso e resultados finais gerados com matplotlib.
- Mensagens de desempenho personalizadas ao final do jogo.

## ✨ Funcionalidades

- *Banco de Questões Variado:* Inclui perguntas sobre operações básicas, raiz quadrada, porcentagem, álgebra simples, geometria e sequências.
- *Seleção Aleatória de Questões:* Cada partida oferece um conjunto diferente de 10 perguntas, garantindo rejogabilidade.
- *Sistema de Tentativas:* 3 tentativas por pergunta, incentivando o jogador a pensar cuidadosamente.
- *Dicas Úteis:* Cada pergunta possui uma dica associada para auxiliar na resolução.
- *Pontuação Dinâmica:* Ganhe mais pontos acertando na primeira tentativa.
- *Interface Gráfica no Jupyter:* Utiliza widgets HTML e ipywidgets para uma experiência de usuário rica diretamente no ambiente Jupyter Notebook/Lab.
- *Visualização de Progresso:* Uma barra de progresso mostra o quão perto você está de completar o desafio.
- *Resultados Detalhados:* Ao final do jogo, são exibidos a pontuação final, a pontuação máxima possível e uma mensagem de desempenho.

## 🛠️ Tecnologias Utilizadas

- *Python 3*
- *IPython/Jupyter Notebook:* Para a execução interativa e exibição.
  - IPython.display: Para renderizar HTML e limpar o output.
  - ipywidgets: Para criar os elementos interativos da interface (botões, campos de texto, labels).
- *Matplotlib:* Para gerar os gráficos de progresso e resultados.
- *NumPy:* Utilizado implicitamente por matplotlib para algumas operações.
- *Random:* Para a seleção aleatória das questões.

## 🚀 Como Executar o Jogo

1.  *Ambiente:* Certifique-se de que você tem um ambiente Jupyter Notebook ou JupyterLab configurado com Python.
2.  *Bibliotecas:* Instale as bibliotecas necessárias. Você pode instalá-las usando pip:
    bash
    pip install ipython ipywidgets matplotlib numpy
    
    Se estiver usando JupyterLab, pode ser necessário instalar extensões para ipywidgets:
    bash
    jupyter labextension install @jupyter-widgets/jupyterlab-manager
    
3.  *Copie o Código:* Cole todo o código Python fornecido em uma única célula de um Jupyter Notebook.
4.  *Execute a Célula:* Execute a célula. O jogo "Math Quest: Aventura Matemática" será iniciado automaticamente abaixo da célula.
5.  *Jogue!*
    -   Leia a pergunta exibida.
    -   Digite sua resposta no campo "Digite sua resposta".
    -   Clique em "Enviar" para verificar sua resposta.
    -   Se precisar de ajuda, clique em "Mostrar Dica".
    -   Siga as instruções e tente obter a maior pontuação!

## 🔧 Estrutura do Código

O jogo é encapsulado na classe MathQuestGame:

-   *__init__(self):*
    -   Define o banco de todas as questões disponíveis (all_available_questions). Cada questão é um dicionário com "question", "answer" e "hint".
    -   Seleciona aleatoriamente num_questions_to_play (atualmente 10) questões para a partida.
    -   Inicializa o estado do jogo: questão atual, pontuação, tentativas restantes, etc.
    -   Chama create_widgets() para configurar os elementos da UI.
    -   Chama show_header() e show_question() para iniciar a primeira pergunta.

-   *create_widgets(self):*
    -   Cria todos os widgets ipywidgets (labels, campos de texto, botões, output para gráficos).
    -   Define as ações (callbacks) para os botões "Enviar" e "Mostrar Dica".

-   *show_header(self):*
    -   Exibe o título estilizado do jogo usando HTML e CSS.
    -   Chama update_score_display().

-   *update_score_display(self):*
    -   Atualiza o widget que mostra a pontuação atual, o número da questão e as tentativas restantes.

-   *show_question(self):*
    -   Limpa o output anterior.
    -   Exibe o cabeçalho.
    -   Apresenta a pergunta atual.
    -   Reseta o campo de resposta e a label de dica.
    -   Reseta as tentativas para 3.
    -   Atualiza a exibição da pontuação.
    -   Plota o gráfico de progresso.
    -   Organiza e exibe todos os widgets relevantes.

-   *plot_progress(self):*
    -   Usa matplotlib para desenhar uma barra de progresso horizontal.

-   *show_hint(self, _):*
    -   Exibe a dica associada à pergunta atual.

-   *check_answer(self, _):*
    -   Valida a entrada do usuário (deve ser um inteiro).
    -   Verifica se a resposta está correta.
    -   Se correta: adiciona pontos (baseado nas tentativas restantes) e avança para a próxima pergunta.
    -   Se incorreta: decrementa as tentativas. Se ainda houver tentativas, informa o jogador. Se não, mostra a resposta correta e avança para a próxima pergunta.

-   *next_question(self):*
    -   Incrementa o contador da questão atual.
    -   Se houver mais perguntas, chama show_question().
    -   Caso contrário, chama show_final_results().

-   *show_final_results(self):*
    -   Limpa o output.
    -   Exibe um cabeçalho de "Jogo Concluído".
    -   Calcula a pontuação máxima possível e a porcentagem de acerto.
    -   Exibe uma mensagem de desempenho baseada na porcentagem.
    -   Usa matplotlib para plotar um gráfico de barras comparando a pontuação do jogador com a pontuação máxima.
    -   Exibe um resumo final com a pontuação e a mensagem de desempenho.

## 🎨 Personalização

Você pode facilmente personalizar o jogo:

-   *Adicionar/Modificar Perguntas:* Edite a lista all_available_questions no método __init__ da classe MathQuestGame. Siga o formato de dicionário existente:
    python
    {
        "question": "Sua nova pergunta aqui?",
        "answer": RESPOSTA_NUMERICA,
        "hint": "Sua dica aqui."
    }
    
-   *Número de Questões por Partida:* Altere o valor da variável num_questions_to_play no método __init__ para definir quantas perguntas serão selecionadas aleatoriamente para cada jogo.
-   *Estilo:* Modifique as tags <style> dentro das strings HTML nos métodos show_header e show_final_results para alterar a aparência do jogo.


