2024-08-07 - 21:38
Status:
Tags: [[NLP]] [[Data Science]]
# Spell Checker

The `SpellChecker` Python library is used for detecting and correcting misspelled words in a text. It is simple to use and can be easily integrated into various text processing tasks.
### Code Example

```python
from spellchecker import SpellChecker

# Initialize the SpellChecker
spell = SpellChecker()

# List of words to check
words = ["recieve", "occuring", "somthing", "wierd", "words"]

# Find the misspelled words
misspelled = spell.unknown(words)

# Print the original words and their corrections
for word in misspelled:
    print(f"Misspelled word: {word}, Suggested correction: {spell.correction(word)}")

# Get a list of likely suggestions for a misspelled word
for word in misspelled:
    suggestions = spell.candidates(word)
    print(f"Suggestions for '{word}': {suggestions}")

```

### Output

The output will look something like this:

```
Misspelled word: recieve, Suggested correction: receive
Misspelled word: occuring, Suggested correction: occurring
Misspelled word: somthing, Suggested correction: something
Misspelled word: wierd, Suggested correction: weird
Suggestions for 'recieve': {'receive', 'deceive'}
Suggestions for 'occuring': {'occurring'}
Suggestions for 'somthing': {'something'}
Suggestions for 'wierd': {'weird'}
```


# Reference