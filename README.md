# name-is-required

## Here Is My Idea

Convince an AI LLM with a medieval personality that you are who you say you are.

The twist: the name you enter at the beginning is completely meaningless. The knight does not care what your name is. Instead, you must prove your identity by helping him understand strange concepts from a distant future.

Only after satisfying all of the knight's requirements will he grant you a completely new name of his own choosing.

**Example:**

> "Congratulations, your new name is Prince of the Nine Powerlines."

---

## Tech Stack

- Vercel
- Next.js
- Groq API

### Alternative

- Ollama (local LLM hosting)
  - More complex setup
  - No external API dependency

---

## Frontend

### The Knight

A medieval knight acts as the primary character and conversational partner.

Ideas:

- Knight sprite or PNG with simple animations
- Different poses depending on mood or conversation state
- Slight shaking/bobbing animation while speaking
- Castle-themed background

### Chat History

- Conversation history window
- Older messages gradually fade away
- Keeps the UI focused on the current discussion

### Input Area

- Text box for user responses
- Standard chat-style interaction

---

## Game Controller

The player must teach the knight a collection of concepts before he will acknowledge their identity.

The knight should naturally guide the conversation toward concepts he does not understand.

### Example Concepts

- Internet
- Cars
- Colors
- Electricity
- Computers
- Additional random modern ideas

---

## Gameplay Loop

1. User enters a name.
2. Knight ignores the name and begins questioning strange future concepts.
3. User attempts to explain concepts in a way a medieval knight would understand.
4. The LLM determines whether the knight understands each required concept.
5. Once all concepts are understood, the knight grants the player a completely new name.
6. Game ends.

---

## LLM Design

The backend should return:

- The knight's dialogue
- The current knowledge requirement
- Whether the knight now understands that concept

### Example Response

```json
{
  "response": "Oh my, dost thou have a horse that is round?",
  "currentKnowledgeRequirement": "cars",
  "understood": false
}
```

---

## Knowledge Requirements

The game maintains a list (or stack) of concepts that the knight must understand.

Example:

```json
[
  {
    "concept": "internet",
    "understood": true
  },
  {
    "concept": "cars",
    "understood": false
  },
  {
    "concept": "colors",
    "understood": false
  }
]
```

The LLM should:

1. Stay in character as a medieval knight.
2. Respond naturally to the player's explanations.
3. Determine if the current concept has been successfully explained.
4. Move to the next concept once understanding is achieved.
5. Eventually generate a ridiculous fantasy-style name for the player.

---

## Example Victory Screen

```text
Well done, traveler.

Though thou didst arrive claiming to be "Nathan",
thy deeds have proven worthy of greater titles.

Henceforth thou shalt be known as:

PRINCE OF THE NINE POWERLINES

```
