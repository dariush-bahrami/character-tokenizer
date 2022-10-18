# character-tokenizer

A character tokenizer for Hugging Face Transformers!

*Note: this code is inspired by Hugging Face [CanineTokenizer](https://github.com/huggingface/transformers/blob/v4.23.1/src/transformers/models/canine/tokenization_canine.py#L63)*

## Example

```py
import string
from charactertokenizer import CharacterTokenizer

chars = string.ascii_letters # This character vocab!
model_max_length = 2048
tokenizer = CharacterTokenizer(chars, model_max_length)
```

Now you can use it to tokenize any string:

```py
example = "I love NLP!"
tokens = tokenizer(example)
print(tokens)
```

Output:

```
{
    "input_ids": [0, 41, 6, 18, 21, 28, 11, 6, 46, 44, 48, 6, 1],
    "token_type_ids": [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    "attention_mask": [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
}
```

And like any other tokenizer in Hugging Face you can decode tokens as follow:

```py
print(tokenizer.decode(tokens["input_ids"]))
```

Output:

```
[CLS]I[UNK]love[UNK]NLP[UNK][SEP]
```

In this example space character and exclamation mark, !, are not in the known characters and therefore will be replaced with unknown special token [UNK].