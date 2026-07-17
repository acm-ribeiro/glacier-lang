
<table align="center">
  <tr>
    <td>
<pre style="color: purple; background: transparent; border: 2px solid purple; border-radius: 10px;">
               _/\_         _/\_
          _/\_/    \_/\_/\_/    \_/\
      _/\_/                        \_\_/\
  ___/                                  \___
 /__________________________________________\
 /         █▀▀ █   ▄▀█ █▀▀ █ █▀▀ █▀█        \
 /         █▄█ █▄▄ █▀█ █▄▄ █ ██▄ █▀▄        \
 /__________________________________________\
 \\\\      ////      ////      ////      ////
  \\\\____////______////______////______////
</pre>
    </td>
  </tr>
</table>


<div align="center">
  <span style="font-size: 2em; font-weight: bold;">
    Gʟᴀᴄɪᴇʀ Language Support for Visual Studio Code
  </span>
</div>

---

## Features

- Syntax highlighting for `.glc` files
- HTTP operation headers such as `GET`, `POST`, `PUT`, and `DELETE`
- Glacier sections including `invariants`, `requires`, and `ensures`
- Expression keywords such as `for`, `exists`, `in`, and `previous`
- Built-in operations including:
  - `request_body`
  - `response_body`
  - `response_code`
  - `path_param`
  - `query_param`
- Highlighting for booleans, null-like values, response codes, integers, operators, and dot-prefixed member access
- YAML syntax support for the surrounding document structure
- Editor comment commands for `//` line comments and `/* ... */` block comments
- Automatic closing and surrounding pairs for brackets and quotes

## Example

```glacier
invariants:
  - response_code(this) == 200

POST /orders:
  requires:
    - request_body(this).quantity > 0
  ensures:
    - response_code(this) == 201 && response_body(this).status != nil

GET /orders/{id}:
  requires:
    - path_param(this["id"]) != nil
  ensures:
    - for x in response_body(this) : x.status == "created"
```

## Installation for Local Development

1. Clone the repository:

   ```bash
   git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
   cd YOUR-REPOSITORY
   ```

2. Open the project in Visual Studio Code:

   ```bash
   code .
   ```

3. Press `F5` to launch an Extension Development Host window.

4. Open or create a file ending in `.glc` to test the extension.

## Project Structure

```text
.
├── package.json
├── language-configuration.json
├── syntaxes/
│   └── glacier.tmLanguage.json
├── test1.glc
├── CHANGELOG.md
├── LICENSE.md
└── README.md
```

- `package.json` registers the Glacier language and grammar with VS Code.
- `language-configuration.json` defines comments, brackets, and auto-closing pairs.
- `syntaxes/glacier.tmLanguage.json` contains the TextMate grammar used for syntax highlighting.
- `test1.glc` provides a sample file for manual extension testing.
- `CHANGELOG.md` records notable changes by release.
- `LICENSE.md` contains the MIT License terms.

## Supported Syntax

### HTTP operations

```glacier
GET /orders/{id}:
POST /orders:
PUT /orders/{id}:
DELETE /orders/{id}:
```

### Specification sections

```glacier
invariants:
requires:
ensures:
```

### Expressions

```glacier
response_code(this) == 200
request_body(this).quantity > 0
path_param(this["id"]) != nil
for x in response_body(this) : x.status == "created"
```

## Requirements

- Visual Studio Code `1.125.0` or later, as specified by the extension manifest

## Extension Settings

This extension does not currently contribute any user-configurable settings.

## Known Limitations

- The extension currently provides grammar-based syntax highlighting and basic language configuration only.
- It does not yet provide diagnostics, validation, formatting, completion suggestions, hover information, or navigation features.
- Syntax recognition is limited to the patterns currently defined in the TextMate grammar.
- Dot-prefixed identifiers such as `.status` are highlighted as member access; general function-call parsing is not currently implemented.
- Comment delimiters are configured for VS Code editing commands, but the grammar does not define dedicated comment scopes.

## Development

The extension is declarative and does not require a build step for grammar changes.

After editing `package.json`, `language-configuration.json`, or the TextMate grammar:

1. Return to the original VS Code window.
2. Restart the Extension Development Host, or reload it with `Ctrl+R` on Windows/Linux or `Cmd+R` on macOS.
3. Reopen a `.glc` file and verify the highlighting behavior.

## Packaging

To package the extension, install the Visual Studio Code Extension Manager:

```bash
npm install --global @vscode/vsce
```

Then run:

```bash
vsce package
```

This creates a `.vsix` package that can be installed locally or prepared for publishing.

## Release Notes

### 0.0.1

- Initial Glacier language registration
- Added `.glc` file recognition
- Added TextMate-based syntax highlighting
- Added comment, bracket, quote, and auto-closing configuration

See [CHANGELOG.md](CHANGELOG.md) for future updates.

## Contributing

Issues and pull requests are welcome. When adding syntax support, include a representative `.glc` example and verify it in the Extension Development Host.

## License

This project is licensed under the MIT License—see the [LICENSE.md](LICENSE.md) file for details.
