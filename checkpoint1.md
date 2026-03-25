1. O Contrato de Identidade (Path Arguments)
   Quando mudamos a rota para perfil/{usuario}, deixamos de tratar o nome como um "detalhe" e passamos a tratá-lo como a identidade da tela.
Na prática: O Jetpack Compose entende que a tela de Perfil não tem razão de existir sem um dono. É um "contrato" rígido: se você tentar navegar para o perfil sem passar o nome, o app simplesmente não encontra o caminho. Isso evita que você chegue em uma tela vazia ou com erro de carregamento.

2. Flexibilidade com Intenção (Query Parameters)
   A mudança na tela de pedidos para pedidos?categoria={categoria} introduziu a ideia de contexto opcional.
Na prática: É como se a tela de Pedidos fosse uma sala multiuso. Se você entrar nela sem dizer nada, ela assume a configuração "Geral" (o defaultValue). Mas, se você entrar "gritando" uma categoria específica, ela se molda para mostrar apenas aquilo. Tecnicamente, isso reduz a criação de múltiplas telas parecidas, centralizando a lógica em um único componente inteligente.

3. Comunicação Ativa entre Telas (Dynamic Routing)
   Ao criar o botão de "Pedidos Eletrônicos", implementamos a passagem de estado via URI.
Na prática: Em vez de a tela de pedidos ter que "adivinhar" o que o usuário quer, o botão já envia a instrução completa. O navController funciona como um garçom: ele leva o pedido (a string com o parâmetro) e entrega exatamente o que foi solicitado para a cozinha (o NavHost), garantindo que o dado chegue íntegro e tipado.

4. O Sistema de Camadas (Hybrid Routes & NavType)
   A última evolução (perfil/{usuario}?idade={idade}) transformou a navegação em um sistema de camadas de informação.
Na prática:
A Primeira Camada (Obrigatória) define quem estamos vendo.
A Segunda Camada (Opcional/Tipada) refina o que sabemos sobre ele.
Ao usar o NavType.IntType, o Kotlin para de tratar tudo como texto genérico e passa a entender números como números. Isso é "humano" porque evita que o desenvolvedor tenha que converter textos manualmente o tempo todo, diminuindo a chance de o app travar por um erro de digitação.