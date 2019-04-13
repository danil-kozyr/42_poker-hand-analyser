# 42_poker-hand-analyser

A poker hand evaluation system that parses and ranks five-card poker hands according to standard poker rules, implemented in C.

## 📖 About

**Poker Hand Analyser** takes a five-card poker hand as input and determines its rank according to standard poker hand rankings, from high card to royal flush.

## 🚀 Features

- **Hand Parsing**: Reads and validates five-card poker hands
- **Card Validation**: Ensures valid faces and suits
- **Duplicate Detection**: Prevents illegal duplicate cards
- **Hand Ranking**: Determines poker hand strength
- **Complete Coverage**: Handles all standard poker hands
- **Error Handling**: Comprehensive input validation

## 🔧 Build Instructions

### Prerequisites

- GCC compiler, Make

### Compilation

```bash
make                # Build the project
make clean         # Clean object files
make fclean        # Clean everything
make re            # Rebuild everything
```

## 📝 Usage

```bash
# Analyze a poker hand
./poker_analyser "2H 3D 5S 9C KD"

# Test different hand types
./poker_analyser "AH KH QH JH 10H"  # Royal flush
./poker_analyser "2C 2D 2H 2S 3C"   # Four of a kind
./poker_analyser "AC AD AH KS KC"   # Full house
```

### Input Format

Space-separated list of five playing cards:

- **Faces**: 2, 3, 4, 5, 6, 7, 8, 9, 10, J, Q, K, A
- **Suits**: H (hearts), D (diamonds), C (clubs), S (spades)
- **Example**: "2D 3H 5S 9C KD"

### Output

One of the following poker hand rankings:

- Royal flush
- Straight flush
- Four of a kind
- Full house
- Flush
- Straight
- Three of a kind
- Two pair
- One pair
- No pair

## 🔍 Implementation Details

### Card Representation

- **Face Values**: 2-10, J(11), Q(12), K(13), A(14)
- **Suit Encoding**: H, D, C, S mapped to integers
- **Card Structure**: Face and suit stored efficiently

### Hand Analysis Process

1. **Parse Input**: Extract individual cards from string
2. **Validate Cards**: Check face/suit validity and duplicates
3. **Sort Hand**: Order cards by face value
4. **Detect Patterns**: Check for pairs, straights, flushes
5. **Rank Hand**: Determine highest applicable ranking

### Ranking Algorithm

```c
// Hand evaluation priority (highest to lowest)
1. Royal Flush    - A, K, Q, J, 10 all same suit
2. Straight Flush - Five consecutive cards, same suit
3. Four of a Kind - Four cards of same rank
4. Full House     - Three of a kind + pair
5. Flush          - Five cards of same suit
6. Straight       - Five consecutive cards
7. Three of a Kind - Three cards of same rank
8. Two Pair       - Two different pairs
9. One Pair       - Two cards of same rank
10. No Pair       - Highest card wins
```

## 🧪 Testing

```bash
# Test royal flush
./poker_analyser "AH KH QH JH 10H"

# Test straight flush
./poker_analyser "5C 6C 7C 8C 9C"

# Test four of a kind
./poker_analyser "2C 2D 2H 2S 3C"

# Test full house
./poker_analyser "AC AD AH KS KC"

# Test flush
./poker_analyser "2H 4H 6H 8H 10H"

# Test straight
./poker_analyser "5C 6D 7H 8S 9C"

# Test three of a kind
./poker_analyser "2C 2D 2H 5S 7C"

# Test two pair
./poker_analyser "2C 2D 5H 5S 7C"

# Test one pair
./poker_analyser "2C 2D 5H 7S 9C"

# Test no pair
./poker_analyser "2C 4D 6H 8S 10C"
```

### Error Cases

```bash
# Invalid face
./poker_analyser "XH 2D 3C 4S 5H"

# Invalid suit
./poker_analyser "2X 2D 3C 4S 5H"

# Duplicate cards
./poker_analyser "2H 2H 3C 4S 5H"

# Wrong number of cards
./poker_analyser "2H 3D 4C 5S"
```

## 🎯 Algorithm Complexity

- **Time Complexity**: O(1) - Fixed hand size of 5 cards
- **Space Complexity**: O(1) - Constant space usage
- **Performance**: Optimized for single hand evaluation

## 🔗 Dependencies

- **Standard C Library**: Basic I/O and string operations
- **No External Libraries**: Pure C implementation

---

_Card game analysis project demonstrating parsing algorithms, pattern recognition, and systematic rule evaluation._
