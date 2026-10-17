# Sem Impacto — protótipo iOS (SwiftUI)

Este é um ponto de partida funcional em SwiftUI para um app de treino de baixo impacto.

## O que já inclui
- Sessão de 30 minutos: aquecimento, socos retos, ganchos, lenhador sem peso, circuito e desaceleração.
- Cronômetro com começar, pausar, avançar e reiniciar.
- Peso ajustável para uma estimativa aproximada de calorias baseada em MET.
- Progresso da sessão e lista de exercícios.
- Avisos de segurança e meta de 300 kcal apresentada como referência, nunca como garantia.

## Como abrir no Xcode
1. Em um Mac, instale/abra o Xcode.
2. Crie um projeto novo: iOS > App, Interface: SwiftUI, Language: Swift.
3. Defina o nome como `TreinoSemImpacto`.
4. Substitua o conteúdo do arquivo principal Swift pelo conteúdo de `TreinoSemImpactoApp.swift`.
5. Se o Xcode já tiver criado outro arquivo com `@main`, remova-o ou substitua-o para evitar dois pontos de entrada.
6. Escolha um simulador de iPhone e pressione Run. Para instalar no iPhone físico, conecte o aparelho e configure sua equipe de assinatura em Signing & Capabilities.

## Limitações atuais
- Este é o código-fonte de um protótipo, não um app já assinado/publicado na App Store.
- O temporizador funciona enquanto o app está aberto; não implementa execução em segundo plano nem notificações.
- As calorias são uma estimativa simplificada e podem divergir bastante do gasto real.
- Não há conta de usuário, armazenamento persistente, Apple Health ou geração automática de planos ainda.

## Segurança
O app não substitui orientação profissional. O treino deve ser adaptado à capacidade de cada pessoa; interrompa se houver sintomas incomuns.
