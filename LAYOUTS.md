# Keyboard layouts

Layouts are small JSON files. Add one in the app: **Keyboard settings > Add a layout file (.json)**.
Built-in layouts live in `app/src/main/assets/layouts/`; to contribute one, add a file there and open a pull request.

```json
{
  "id": "en",
  "name": "English",
  "voice": "en-US",
  "letters": [
    ["q","w","e","r","t","y","u","i","o","p"],
    ["a","s","d","f","g","h","j","k","l"],
    ["z","x","c","v","b","n","m",",","."]
  ],
  "shift": null,
  "symbols": [
    ["1","2","3","4","5","6","7","8","9","0"],
    ["@","#","$","%","&","-","+","(",")","/"],
    ["*","\"","'",":",";","!","?","=","_","\\"]
  ]
}
```

- `id`: letters, digits, `-` and `_` only (up to 40). A file with the same id as a built-in layout replaces it.
- `name`: shown on the space bar. `voice`: language tag used for voice typing (for example `en-US`, `fr-FR`).
- `letters`: rows of keys. Each key is a string and is typed as written; it can be more than one character.
- `shift` (optional): the same shape as `letters`, giving what each key types with Shift on. If left out, keys are upper-cased.
  Use it for scripts where upper-casing does not apply.
- `symbols`: the number and symbol page, same format.
- Adaptive letter placement only moves keys that start with a letter, so punctuation keys stay where you put them.

The keyboard adds the mic, Shift, 123, space, Del and Enter keys itself. Typing systems that need composition
(for example phonetic input) are not supported by this format yet.
