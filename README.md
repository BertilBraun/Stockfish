# Lightweight Stockfish Fork for MCTS

This is a **stripped-down, optimized fork of the Stockfish Chess Engine**, specifically tailored for use in **Monte
Carlo Tree Search (MCTS)** and **AlphaZero-style reinforcement learning** systems.

## ✨ What's This?

This project provides:

- ✅ Fast **legal move generation**
- ✅ Efficient **board (position) representation**
- ✅ Lightweight, fast **position copying and move application**

It removes everything **not needed** for MCTS-based approaches:

- ❌ No search or evaluation logic
- ❌ No UCI interface or engine loop
- ❌ No neural network integration
- ❌ No undo stack or move history

Instead, this fork focuses purely on **minimal, high-performance functionality** for game simulation and tree expansion.

---

## ⚙️ Why This Exists

For projects using **MCTS in C++**, especially in **reinforcement learning** (like AlphaZero), you typically need:

1. **Fast move generation**
2. **Efficient state transitions**
3. **Low-overhead board copies**

Stockfish's original design maintains extensive internal state for search and evaluation, including stacks for undoing
moves. This fork:

- Removes the **search, evaluation, and history tracking**
- Keeps only the essentials for move generation and state transitions
- Refactors `StateInfo` and `Position` for **trivial copyability and simplicity**

---

## 🧠 Use Case

This fork is designed to be used as a **low-level backend** for a learning agent, such as:

- An AlphaZero-style reinforcement learning setup
- A custom MCTS implementation
- High-throughput self-play environments

📌 See [My DIY Alpha Zero Project](https://github.com/BertilBraun/Advanced-Techniques-in-Chess-Engines) for how this
backend is used in a full learning
pipeline.

---

## 🧩 What's Left from Stockfish?

The following Stockfish components remain:

- `Position` class: Simplified for fast copies and move application
- `MoveGen`: Legal move generation (with checks)
- Basic Zobrist hashing and repetition detection (minimal form)

All other components (search, evaluation, network, UCI, etc.) have been **completely removed or disabled**.

---

## 📦 Integration Example

```cpp
Position pos("startpos"); // or FEN

for (const Move m : MoveList<LEGAL>(pos)) {
    Position next = pos; // fast copy
    next.do_move(m);     // fast transition
    // ... use next in MCTS tree
}
