# Blackjack

:::mermaid
classDiagram
  class Table {
    - String gameType
    - Array betDenominations
    - Number turnCounter
    - String gamePhase
    - Array resultsLog
    - Deck deck
    - Player[] players
    - Player dealer
    + Table(gameType: String, betDenominations: Array)
    + startRound(): void
    + blackjackAssignPlayerHands(): void
    + blackjackClearPlayerHandsAndBets(): void
    + evaluateMove(player: Player): void
    + Player getTurnPlayer(): Player
    + blackjackEvaluateAndGetRoundResults(): String
    + onLastPlayer(): boolean
    + onFirstPlayer(): boolean
    + allPlayerActionsResolved(): boolean
  }
  class Player {
    - String name
    - Card[] hand
    - Number chips
    - Number bet
    - String gameStatus
    + Player(name: String, chips: Number, bet: Number)
    + makeBet(amount: Number): Number
    + takeAction(action: String): String
  }
  class Deck {
    - Card[] cards
    + Deck()
    + shuffle(): void
    + resetDeck(gameType: String): Card[]
    + drawCard(): Card
  }
  class Card {
    - String suit
    - String rank
    + Card(suit: String, rank: String)
    + getRankNumber(): Number
  }

  Table --> Deck
  Table --> Player
  Table --> Player
  Player --> Deck
