### Prefabs
1. Protagonista (Player)
- Descrição: Personagem controlado pelo jogador, responsável por se mover pelo cenário e combater os inimigos.
- Quando é utilizado: Presente em todas as fases do jogo.
- Componentes:
    - Sprite: Spritesheet do protagonista com animações de idle, corrida, soco, chute, pulo e dano
    - Colisor: Capsule Collider 2D (corpo) + Box Collider 2D (hitbox de ataque)
    - Fonte de áudio: Sons de soco, chute e dano recebido
      
- Scripts:
    - PlayerMovement: Controla a movimentação lateral e o pulo do personagem com base no input do jogador
    - PlayerCombat: Gerencia os ataques de soco e chute, ativa a hitbox no momento certo da animação
    - PlayerHealth: Controla a vida do jogador, aplica dano recebido e verifica se a vida chegou a zero
    - SpecialAbility: Controla o desbloqueio e uso da habilidade especial com base no número de inimigos derrotados


2. Inimigo Comum (Enemy)
- Descrição: Membros da organização criminosa que aparecem em ondas ao longo das fases.
- Quando é utilizado: Spawna em ondas durante a progressão das fases.
- Componentes:
    - Sprite: Spritesheet do inimigo com animações de idle, caminhada, ataque e dano
    - Colisor: Capsule Collider 2D (corpo) + Box Collider 2D (hitbox de ataque)
    - Fonte de áudio: Sons de ataque e dano recebido
      
- Scripts:
    - EnemyAI: Controla o comportamento do inimigo, fazendo ele se mover em direção ao jogador e atacar quando estiver próximo
    - EnemyHealth: Controla a vida do inimigo e verifica quando ele é derrotado
    - EnemyCombat: Gerencia os ataques do inimigo e ativa a hitbox no momento correto


3. Boss
- Descrição: Inimigo mais forte que aparece ao final de cada fase, com mais vida e ataques mais poderosos.
- Quando é utilizado: Spawna ao final de cada fase, após todas as ondas de inimigos serem derrotadas.
- Componentes:
    - Sprite: Spritesheet do boss com animações de idle, ataque, dano e derrota
    - Colisor: Capsule Collider 2D (corpo) + Box Collider 2D (hitbox de ataque)
    - Fonte de áudio: Sons de ataque, dano recebido e derrota
      
- Scripts:
    - BossAI: Comportamento mais complexo que o inimigo comum, com padrões de ataque variados
    - BossHealth: Controla a vida do boss, atualiza a barra de vida na HUD e verifica quando é derrotado
    - BossPhase: Altera o comportamento do boss conforme ele perde vida (ex: fica mais agressivo na metade da vida)


4. Item Coletável (Collectible)
- Descrição: Itens espalhados pelo cenário que o jogador pode coletar para recuperar vida ou obter bônus.
- Quando é utilizado: Posicionado pelo cenário durante o design das fases.
- Componentes:
    - Sprite: Sprite do item (ex: comida, kit médico)
    - Colisor: Box Collider 2D com "Is Trigger" ativado
    - Fonte de áudio: Som de coleta
      
- Scripts:
    - ItemCollect: Detecta quando o jogador entra em contato com o item, aplica o efeito (restaurar vida ou bônus) e destroi o objeto

5. Gerador de Ondas (WaveSpawner)
- Descrição: Objeto invisível responsável por controlar o surgimento dos inimigos em ondas durante a fase.
- Quando é utilizado: Presente em todas as fases, ativado conforme o jogador avança no cenário.
- Componentes:
    - Sprite: Nenhum (objeto invisível)
    - Colisor: Nenhum
    - Fonte de áudio: Nenhuma
      
- Scripts:
    - WaveSpawner: Controla quais inimigos spawnam, em qual quantidade e em qual momento da fase. Verifica quando todos os inimigos de uma onda foram derrotados para liberar o avanço do jogador ou iniciar a próxima onda


6. HUD
- Descrição: Interface visual que exibe as informações do jogador na tela.
- Quando é utilizado: Presente em todas as fases.
- Componentes:
    - Sprite: Ícones de vida, pontuação e habilidade especial
    - Colisor: Nenhum
    - Fonte de áudio: Nenhuma
      
- Scripts:
    - HUDManager: Atualiza em tempo real as informações de vida, pontuação e status da habilidade especial com base nos dados do jogador
