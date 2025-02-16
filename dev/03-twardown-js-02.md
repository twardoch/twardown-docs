TWARDOWN - Twardoch’s Markdown flavor

Below is an answer that addresses both parts of your question.

---

## 1. Using a Global Configuration with vscode-remark

By default, the vscode-remark extension looks for a remark configuration file inside your workspace
(for example, as a file named `.remarkrc`, `.remarkrc.yml`, or even in your project’s package.json
under a “remarkConfig” key). There isn’t (yet) a built‐in “global remark config” file that the
extension automatically looks up in your user folder (like
`~/Library/Application Support/Code/User/settings.json` on macOS).

However, you have a couple of options:

- **Make the Extension Always Run:**  
  The extension has a setting called `remark.requireConfig` (which defaults to `false`). If you set
  this to `true` in your user settings, then the extension will only run when – and only when – it
  finds a configuration file in the workspace. If you leave it as `false` (or don’t set it), then it
  will run using its default behavior.  
  You could (if you wish) create a “global” config file in your HOME folder and, for every project,
  symlink it (or copy it) into the workspace.
- **Customize User Settings for VS Code:**  
  You might also add remark-related defaults directly into your VS Code User Settings for markdown
  formatting. See the extension’s documentation for settings such as the default formatter. (For
  example, setting the formatter globally with the configuration below makes VS Code use
  vscode-remark for all Markdown files.)
  ```json
  {
    "[markdown]": {
      "editor.defaultFormatter": "unifiedjs.vscode-remark",
      "editor.formatOnSave": true
    }
  }
  ```

For now there is no “global remarkrc” facility that lives outside a workspace. Ultimately, if you’d
like a truly global configuration, you might consider opening a feature request on the
[vscode-remark GitHub repository](https://github.com/remarkjs/vscode-remark) or check whether the
language server (remark-language-server) provides fallback to a global installation (see related
issues on GitHub).

---

## 2. An Annotated and Exquisite `.remarkrc.yml`

Below is an example of a well-organized, annotated `remarkrc.yml` file. You can save it in your
project root (or in any supported configuration file name) so that vscode-remark (and remark-cli)
will pick it up.

```yaml
# =============================================================================
# Remark Configuration File
# =============================================================================
# This configuration file tells remark how to process markdown files.
# It enables a set of plugins for linting, formatting, and various markdown
# syntaxes. You can adjust each plugin’s options as needed.
#
# Save this file as:
#   .remarkrc.yml
# in your project’s root. There is currently no built-in way to specify a
# global configuration file outside of a workspace.
# =============================================================================

# Enable output; when set to true, remark will produce output after processing.
output: true

# -----------------------------------------------------------------------------
# Plugins
# -----------------------------------------------------------------------------
plugins:
  # ---------------------------------------------------------------------------
  # Frontmatter Plugin
  # Parses YAML, TOML (or other) front matter found at the top of markdown files.
  frontmatter: {}

  # ---------------------------------------------------------------------------
  # GitHub Plugin
  # Automatically links GitHub commit ids, issues, pull requests, and mentions.
  github:
    repository: 'yourusername/yourrepo' # Replace with your repository identifier.
    mentionStrong: false # Use normal (non-bold) formatting for mentions.

  # ---------------------------------------------------------------------------
  # Validate Links Plugin
  # Checks that links referenced in the markdown actually resolve.
  validate-links:
    repository: 'yourusername/yourrepo-wiki' # Optionally specify a repository for wiki links.

  # ---------------------------------------------------------------------------
  # Heading Gap Plugin
  # Adjusts the vertical spacing before and after headings.
  heading-gap:
    '1': # Options for level 1 headings.
      before: "\n\n" # Two line breaks before the heading.
      after: "\n" # One line break after the heading.
    '2': # Options for level 2 headings.
      before: "\n" # One line break before the heading.
      after: "\n" # One line break after the heading.

  # ---------------------------------------------------------------------------
  # Inline Links Plugin
  # Transforms reference-style links into inline links.
  inline-links: {} # No options are needed for defaults.

  # ---------------------------------------------------------------------------
  # Slug Plugin
  # Adds slug information to headings (good for creating anchors).
  slug: {} # Uses default options.

  # ---------------------------------------------------------------------------
  # Squeeze Paragraphs Plugin
  # Removes extra blank paragraphs that might have been generated.
  squeeze-paragraphs: {} # Simply remove extra empty paragraphs.

  # ---------------------------------------------------------------------------
  # YAML Config Plugin
  # Lets remark load additional YAML configuration from markdown files.
  yaml-config: {} # Enable YAML configuration parsing.

  # ---------------------------------------------------------------------------
  # Autolink Headings Plugin
  # Automatically adds links (anchors) to headings.
  autolink-headings: {} # Uses default options.

  # ---------------------------------------------------------------------------
  # Embed Images Plugin
  # Supports embedding images by converting local files to base64 strings.
  embed-images: {} # Default behavior embeds images.

  # ---------------------------------------------------------------------------
  # External Links Plugin
  # Modifies external links to include target attributes so they open in new tabs.
  external-links:
    target: '_blank' # Opens external links in a new browser tab.

  # ---------------------------------------------------------------------------
  # Gemoji Plugin
  # Replaces GitHub emoji shortcodes (like :smile:) with actual emoji characters.
  gemoji: {} # Uses default emoji mapping.

  # ---------------------------------------------------------------------------
  # HTML Output Plugin
  # Serializes markdown to HTML. Uncomment if you need to convert markdown to HTML.
  html: {}

  # ---------------------------------------------------------------------------
  # Parse YAML Plugin
  # Explicitly parses YAML blocks in your Markdown if they are not standard front matter.
  parse-yaml: {}

  # ---------------------------------------------------------------------------
  # Lint Plugin
  # Checks your markdown files against a set of linting rules.
  lint: {} # Add specific linting rules as needed.

# -----------------------------------------------------------------------------
# Settings for Markdown Parsing and Formatting
# -----------------------------------------------------------------------------
settings:
  # Bullet style for lists (can be "-" or "*" etc.)
  bullet: '-'
  # Whether to use a closing sequence for ATX headings (set to true to append a closing hash).
  closeAtx: false
  # Enable CommonMark parsing standard; set to true if you want stricter CommonMark behavior.
  commonmark: false
  # Characters used to denote emphasis; typically "_" or "*" are common choices.
  emphasis: '_'
  # Whether or not to parse HTML entities in the markdown text.
  entities: false
  # Code fence delimiter (backticks in most cases).
  fence: '`'
  # Enable support for fenced code blocks.
  fences: true
  # Enable support for footnotes.
  footnotes: true
  # Use GitHub Flavored Markdown (GFM) extensions.
  gfm: true
  # Automatically increment list markers.
  incrementListMarker: true
  # Indentation for list items (“1” means one level of indentation).
  listItemIndent: '1'
  # Whether to use a looser table syntax.
  looseTable: false
  # Whether to add padding to table cells.
  paddedTable: true
  # Use pedantic parsing for legacy markdown behavior.
  pedantic: false
  # Character to be repeated to create a horizontal rule (thematic break).
  rule: '-'
  # How many times the rule character is repeated (commonly 3).
  ruleRepetition: 3
  # Whether to enforce spaces around the rule characters.
  ruleSpaces: false
  # Use Setext-style (underlined) headings instead of ATX (hash prefixed) headings.
  setext: false
  # Require spacing in tables.
  spacedTable: true
  # Character to denote strong (bold) text; typically "*" is used.
  strong: '*'
  # Whether or not YAML front matter should be processed.
  yaml: true
```

---

### Explanation of the YAML Structure

- **Top-Level Options:**  
  The `output` key enables or disables producing output from the processing run.

- **Plugins Section:**  
  Under `plugins`, each plugin is listed (using either a mapping with options or an empty object
  `{}` if no options are needed). Comments explain what each plugin does so you can later adjust its
  options if necessary.

- **Settings Section:**  
  These control how remark parses and formats markdown. For instance, you can specify how lists are
  indented, what style of headings to use, and whether to apply GitHub Flavored Markdown (GFM).

Feel free to add, remove, or tweak plugins and settings based on the particular standards you want
your project to follow. This annotated file is an excellent starting point when using the
vscode-remark extension to lint and format your markdown files.

---

With these details, you should be able to both understand how (and where) to use a configuration for
vscode-remark and have a beautifully annotated sample configuration to customize your markdown
processing.

Below is our analysis and answer:

---

### Global Configuration in VS Code for vscode-remark

The vscode-remark extension (which powers remark-language-server) is designed to pick up a
configuration file from your workspace (or a parent folder) such as a `.remarkrc`, `.remarkrc.yml`,
or even a `remarkConfig` field in your project’s package.json. It does not support defining a full
remark configuration directly in VS Code’s global settings (e.g. in your user-level settings.json
located at `~/Library/Application Support/Code/User/settings.json`). You can only control one global
flag – for example, the setting `"remark.requireConfig"` tells the extension whether to run only
when it finds a config file—but the detailed configuration must reside in a dedicated configuration
file in your project.  
cite83†, cite82†

---

### An Exquisite, Annotated `.remarkrc.yml` Configuration File

Below is a carefully organized and annotated YAML configuration file for remark. You can place this
file in your workspace (or a parent folder) so that the vscode-remark extension picks it up
automatically. Adjust repository names and any options as needed for your project.

```yaml
# .remarkrc.yml
# ============================================
# This file configures remark for linting and formatting Markdown.
# It is used both by remark-cli and the VSCode extension vscode-remark.
# Place this file in your project root so that it is automatically detected.
# ============================================

# Enable output formatting so that remark writes the transformed Markdown.
output: true

# --------------------------------------------
# Plugins Section: List all remark plugins to apply.
# --------------------------------------------
plugins:
  # Parse YAML frontmatter at the start of markdown files.
  - frontmatter

  # GitHub plugin:
  # Automatically transforms references (issues, commits, user mentions) into links.
  - github:
      # Set your repository (change this to match your repository if needed).
      repository: 'yourusername/yourrepo'
      # Disable strong mention if you prefer plain mentions.
      mentionStrong: false

  # Validate links:
  # Checks that all URLs and relative links are valid.
  - validate-links:
      # Optional: set repository for resolving relative links.
      repository: 'yourusername/yourrepo'

  # Heading gap:
  # Adjust spacing before and after headings to enforce a consistent style.
  - heading-gap:
      '1': # For level-1 headings:
        before: "\n\n" # Two newlines before the heading.
        after: "\n" # One newline after the heading.
      '2': # For level-2 headings:
        before: "\n" # One newline before.
        after: "\n" # One newline after.

  # Inline links:
  # Converts reference-style link definitions into inline links.
  - inline-links

  # Slug:
  # Generates URL-friendly slugs from headings (useful for linking).
  - slug

  # Squeeze paragraphs:
  # Removes redundant blank lines from paragraphs.
  - squeeze-paragraphs

  # YAML config:
  # Allows remark to load configuration from YAML files.
  - yaml-config

  # Autolink headings:
  # Automatically adds clickable anchor links to headings.
  - autolink-headings

  # Embed images:
  # Converts local image references into base64-encoded data URIs.
  - embed-images

  # External links:
  # Processes external links so that they open in a new browser tab.
  - external-links:
      target: '_blank' # Sets the target attribute to "_blank".

  # Gemoji:
  # Transforms GitHub emoji shortcodes (e.g. :smile:) into Unicode emoji.
  - gemoji

  # HTML:
  # Serializes the Markdown content as HTML if needed.
  - html

  # Parse YAML:
  # Processes YAML content in markdown (such as frontmatter) and exposes it.
  - parse-yaml

  # Table of Contents:
  # Automatically generates a TOC based on the headings in the document.
  - toc

  # Lint:
  # Runs remark-lint to check Markdown for style and syntax issues.
  - lint

  # Additional lint rule overrides:
  - lint-alphabetize-lists: false # Do not enforce alphabetization of list items.
  - lint-heading-increment: true # Ensure headings increment by only one level at a time.
  - lint-no-consecutive-blank-lines: true # Disallow multiple blank lines in a row.

# --------------------------------------------
# Settings Section: Controls output formatting.
# These options affect how remark-stringify converts the Markdown AST back to text.
# --------------------------------------------
settings:
  bullet: '*' # Use asterisk (*) for unordered list bullets.
  fence: '`' # Use backticks for fenced code blocks.
  strong: '**' # Use double asterisks for bold text.
  emphasis: '_' # Use underscores for italic text.
  closeAtx: false # Do not append closing '#' characters to ATX headings.
  gfm: true # Enable GitHub Flavored Markdown features.
  incrementListMarker: true # Automatically increment numbers for ordered lists.
  listItemIndent: '1' # Use one space to indent list items.
  rule: '-' # Use a hyphen for thematic breaks.
  ruleRepetition: 3 # Repeat the rule character three times for a horizontal rule.

# ============================================
# End of configuration.
# ============================================
```

---

### Summary

• **Global Config:** Unfortunately, you cannot define a full remark configuration in VS Code’s
global settings.json. Instead, vscode-remark requires a dedicated configuration file (like the one
above) placed in your workspace.  
• **.remarkrc.yml:** The sample YAML above is fully commented and organized so that you can adjust
it to your needs.

This configuration file works seamlessly with the vscode-remark extension (which uses the same
configuration files as remark-cli) and helps you enforce a consistent Markdown style across your
project.  
cite83†, cite82†

````yaml
# remarkrc.yml
# Configuration file for unifiedjs.vscode-remark VSCode extension.
# This file is used to configure remark-cli and the VSCode extension.
# It defines plugins, their options, and general settings for Markdown processing.
#
# For more information about remark, see: https://github.com/remarkjs/remark
# For a list of available plugins, see: https://github.com/remarkjs/remark/blob/main/doc/plugins.md

output: true
# output: true -  This setting likely controls whether remark outputs the processed Markdown.
#               In the context of VSCode extension, it might be relevant for formatting or linting results display.
#               Setting it to true ensures that the processed output is considered.

plugins:
  # Plugins are used to extend remark's functionality.
  # Each plugin is configured under the 'plugins' section.
  # Plugin names are typically the names used in remark-cli or require statements in JavaScript.

  frontmatter:
  # remark-frontmatter -  Plugin to support frontmatter in Markdown files (YAML, TOML, etc.).
  #                     Frontmatter is metadata at the beginning of the file, commonly used for blog posts, etc.
  #                     See: https://github.com/remarkjs/remark-frontmatter
  #                     No options are specified here, so it uses default behavior (YAML, TOML, and more).

  github:
    # remark-github - Plugin to autolink references to commits, issues, pull requests, and users on GitHub.
    #                 See: https://github.com/remarkjs/remark-github
    repository: Fontlab/fl
    # repository: Fontlab/fl -  Specifies the GitHub repository to link to.
    #                           In this case, it's set to 'Fontlab/fl', likely for a Fontlab project.
    mentionStrong: false
    # mentionStrong: false -  Controls whether mentions (@user) should be rendered as strong text.
    #                        Setting it to false disables making mentions bold.

  'validate-links': # Note: plugin names with hyphens need to be quoted in YAML
    # remark-validate-links - Plugin to check links to headings and files in Markdown.
    #                       Useful for ensuring internal links within documentation are valid.
    #                       See: https://github.com/remarkjs/remark-validate-links
    repository: Fontlab/FontLabVI-help.wiki
    # repository: Fontlab/FontLabVI-help.wiki -  Specifies the repository context for link validation.
    #                                            Links will be validated relative to this repository.

  heading-gap:
    # remark-heading-gap - Plugin to enforce blank lines around headings for better readability.
    #                    See: https://github.com/remarkjs/remark-heading-gap
    '1': # Configuration for level 1 headings (<h1>)
      after: "\n"
      # after: "\n" -  Ensures there is one newline character after level 1 headings.
      before: "\n\n"
      # before: "\n\n" - Ensures there are two newline characters before level 1 headings.
    '2': # Configuration for level 2 headings (<h2>)
      after: "\n"
      # after: "\n" -  Ensures there is one newline character after level 2 headings.
      before: "\n"
      # before: "\n" - Ensures there is one newline character before level 2 headings.
    # ... you can configure gaps for other heading levels (3, 4, 5, 6) similarly if needed.

  inline-links:
  # remark-inline-links - Plugin to convert reference links and images to inline links and images.
  #                      This can simplify Markdown output by inlining links instead of using references at the bottom.
  #                      See: https://github.com/remarkjs/remark-inline-links
  #                      No options are specified, using default behavior.

  slug:
  # remark-slug -  Plugin to add slugs (IDs) to headings. Slugs are used for creating linkable headings (anchors).
  #               Automatically adds IDs to headings based on their text content.
  #               Part of remark-github (https://github.com/remarkjs/remark-github) but can be used standalone.
  #               No options are specified, using default behavior.

  squeeze-paragraphs:
  # remark-squeeze-paragraphs - Plugin to remove empty paragraphs from Markdown.
  #                           Helps to clean up Markdown by removing unnecessary empty lines between paragraphs.
  #                           See: https://github.com/remarkjs/remark-squeeze-paragraphs
  #                           No options are specified, using default behavior.

  'yaml-config': # Note: plugin names with hyphens need to be quoted in YAML
  # remark-yaml-config - Plugin to allow configuration of remark plugins via YAML in comments within Markdown files.
  #                    Enables in-document configuration, which can be useful for specific Markdown files.
  #                    See: https://github.com/remarkjs/remark-yaml-config
  #                    No options are specified, using default behavior.

  'autolink-headings': # Note: plugin names with hyphens need to be quoted in YAML
  # remark-autolink-headings - Plugin to automatically create links from headings to themselves.
  #                          Makes headings clickable and linkable, often used in documentation sites.
  #                          Part of remark-github, but can be used standalone.
  #                          No options are specified, using default behavior.

  embed-images:
  # remark-embed-images - Plugin to embed local images as base64-encoded data URIs directly in the Markdown output.
  #                     Can be useful for creating self-contained Markdown documents.
  #                     See: https://github.com/remarkjs/remark-embed-images
  #                     No options are specified, using default behavior.

  'external-links': # Note: plugin names with hyphens need to be quoted in YAML
    # remark-external-links - Plugin to automatically add attributes to external links.
    #                        Useful for accessibility and security (e.g., opening external links in a new tab).
    #                        See:  (part of remark-github, https://github.com/remarkjs/remark-github)
    target: '_blank'
    # target: "_blank" -  Sets the 'target' attribute of external links to '_blank'.
    #                     This makes external links open in a new tab or window.

  gemoji:
  # remark-gemoji - Plugin to transform Gemoji shortcodes (like :smile:) into actual emoji characters.
  #                See: https://github.com/remarkjs/remark-gemoji
  #                No options are specified, using default behavior.

  html:
  # remark-html - Plugin to serialize the Markdown AST (Abstract Syntax Tree) back into HTML.
  #              This is essential for converting processed Markdown back to HTML output.
  #              See: https://github.com/remarkjs/remark-html
  #              No options are specified, using default behavior (which is to serialize to HTML).

  lint:
  # remark-lint -  Umbrella plugin for remark-lint rules. Enables Markdown style checking and linting.
  #               See: https://github.com/remarkjs/remark-lint
  #               Configurations below are for individual lint rules.
  #               For details on each rule, see: https://github.com/remarkjs/remark-lint/blob/main/readme.md#list-of-rules

  'lint-alphabetize-lists': false
  # lint-alphabetize-lists: false - Rule to enforce alphabetized lists. Disabled here.

  'lint-blockquote-indentation': consistent
  # lint-blockquote-indentation: consistent - Rule to enforce consistent indentation in blockquotes. 'consistent' is a valid option.

  'lint-books-links': true
  # lint-books-links: true - Rule to lint for ISBN-like links. Enabled here.

  'lint-checkbox-character-style': # Rule to enforce checkbox character style.
    checked: x
    # checked: x -  Specifies 'x' as the character for checked checkboxes (e.g., [x]).
    unchecked: ' '
    # unchecked: " " - Specifies a space " " as the character for unchecked checkboxes (e.g., [ ]).

  'lint-checkbox-content-indent': true
  # lint-checkbox-content-indent: true - Rule to enforce consistent indentation of checkbox content. Enabled.

  'lint-code-block-style': fenced
  # lint-code-block-style: fenced - Rule to enforce fenced code blocks (using ```). 'fenced' is the preferred style.

  'lint-definition-case': true
  # lint-definition-case: true - Rule to enforce lowercase definition labels. Enabled.

  'lint-definition-spacing': true
  # lint-definition-spacing: true - Rule to enforce blank lines around definitions. Enabled.

  'lint-emphasis-marker': '_'
  # lint-emphasis-marker: "_" - Rule to enforce underscore (_) as the emphasis marker (e.g., _italic_).

  'lint-fenced-code-flag': # Rule for fenced code block flags (language identifiers).
    allowEmpty: true
    # allowEmpty: true - Allows fenced code blocks without language flags (e.g., ``` ```).

  'lint-fenced-code-marker': '`'
  # lint-fenced-code-marker: "`" - Rule to enforce backtick (`) as the fenced code block marker (```).

  'lint-file-extension': md
  # lint-file-extension: md - Rule to enforce '.md' as the file extension for Markdown files.

  'lint-final-definition': true
  # lint-final-definition: true - Rule to enforce definitions to be placed at the end of the document. Enabled.

  'lint-final-newline': true
  # lint-final-newline: true - Rule to enforce a final newline at the end of the file. Enabled.

  'lint-first-heading-level': 1
  # lint-first-heading-level: 1 - Rule to enforce the first heading level to be <h1> (level 1).

  'lint-hard-break-spaces': true
  # lint-hard-break-spaces: true - Rule to disallow spaces for hard breaks (use two newlines instead). Enabled.

  'lint-heading-increment': true
  # lint-heading-increment: true - Rule to enforce headings to increment by one level at a time (no skipping levels).

  'lint-heading-style': atx
  # lint-heading-style: atx - Rule to enforce ATX heading style (e.g., ## Heading) instead of Setext (e.g., Heading =====).

  'lint-link-title-style': consistent
  # lint-link-title-style: consistent - Rule to enforce consistent link title style (quotes or no quotes). 'consistent' is used.

  'lint-list-item-bullet-indent': false
  # lint-list-item-bullet-indent: false - Rule related to list item bullet indentation. Disabled here.

  'lint-list-item-content-indent': true
  # lint-list-item-content-indent: true - Rule to enforce consistent indentation of list item content. Enabled.

  'lint-list-item-indent': space
  # lint-list-item-indent: space - Rule to enforce space indentation for list items. 'space' is used.

  'lint-list-item-spacing': # Rule for spacing between list items.
    checkBlanks: true
    # checkBlanks: true - Checks for blank lines between list items to enforce consistent spacing.

  'lint-maximum-heading-length': 300
  # lint-maximum-heading-length: 300 - Rule to limit the maximum heading length to 300 characters.

  'lint-maximum-line-length': 120
  # lint-maximum-line-length: 120 - Rule to limit the maximum line length to 120 characters.

  'lint-no-auto-link-without-protocol': false
  # lint-no-auto-link-without-protocol: false - Rule to disallow autolinks without protocols (like 'example.com'). Disabled.

  'lint-no-blockquote-without-caret': false
  # lint-no-blockquote-without-caret: false - Rule related to blockquotes and carets. Disabled.

  'lint-no-blockquote-without-marker': false
  # lint-no-blockquote-without-marker: false - Rule related to blockquotes and markers. Disabled.

  'lint-no-consecutive-blank-lines': true
  # lint-no-consecutive-blank-lines: true - Rule to disallow consecutive blank lines. Enabled.

  'lint-no-dead-urls': false
  # lint-no-dead-urls: false - Rule to check for dead URLs. Can be slow, disabled here.

  'lint-no-duplicate-definitions': true
  # lint-no-duplicate-definitions: true - Rule to disallow duplicate link or image definitions. Enabled.

  'lint-no-duplicate-headings': true
  # lint-no-duplicate-headings: true - Rule to disallow duplicate headings in the same document. Enabled.

  'lint-no-emphasis-as-heading': true
  # lint-no-emphasis-as-heading: true - Rule to disallow using emphasis (bold/italic) as headings. Enabled.

  'lint-no-empty-sections': true
  # lint-no-empty-sections: true - Rule to disallow empty sections (headings without content). Enabled.

  'lint-no-file-name-articles': true
  # lint-no-file-name-articles: true - Rule to disallow articles (a, an, the) in file names. Enabled.

  'lint-no-file-name-consecutive-dashes': true
  # lint-no-file-name-consecutive-dashes: true - Rule to disallow consecutive dashes in file names. Enabled.

  'lint-no-file-name-irregular-characters': '\\.a-zA-Z0-9_\$\-'
  # lint-no-file-name-irregular-characters: '\\.a-zA-Z0-9_\$\-' - Rule to define allowed characters in file names (alphanumeric, underscore, dollar, hyphen, dot).

  'lint-no-file-name-mixed-case': true
  # lint-no-file-name-mixed-case: true - Rule to disallow mixed case file names (enforce lowercase or kebab-case). Enabled.

  'lint-no-file-name-outer-dashes': true
  # lint-no-file-name-outer-dashes: true - Rule to disallow dashes at the beginning or end of file names. Enabled.

  'lint-no-heading-content-indent': true
  # lint-no-heading-content-indent: true - Rule to disallow indentation of heading content. Enabled.

  'lint-no-heading-indent': true
  # lint-no-heading-indent: true - Rule to disallow indentation of headings themselves. Enabled.

  'lint-no-heading-punctuation': false
  # lint-no-heading-punctuation: false - Rule to disallow punctuation at the end of headings. Disabled here.

  'lint-no-html': false
  # lint-no-html: false - Rule to disallow raw HTML in Markdown. Disabled here (allows HTML).

  'lint-no-inline-padding': true
  # lint-no-inline-padding: true - Rule to disallow inline padding (spaces) in Markdown. Enabled.

  'lint-no-literal-urls': false
  # lint-no-literal-urls: false - Rule to disallow literal URLs (like `<http://example.com>`). Disabled.

  'lint-no-missing-blank-lines': true
  # lint-no-missing-blank-lines: true - Rule to enforce blank lines around certain elements (like headings, lists). Enabled.

  'lint-no-multiple-toplevel-headings': true
  # lint-no-multiple-toplevel-headings: true - Rule to disallow multiple top-level headings (<h1>) in a document. Enabled.

  'lint-no-shell-dollars': true
  # lint-no-shell-dollars: true - Rule to disallow dollar signs ($) in shell code examples (use ```shell ``` instead). Enabled.

  'lint-no-shortcut-reference-image': false
  # lint-no-shortcut-reference-image: false - Rule to disallow shortcut reference images. Disabled.

  'lint-no-shortcut-reference-link': false
  # lint-no-shortcut-reference-link: false - Rule to disallow shortcut reference links. Disabled.

  'lint-no-table-indentation': true
  # lint-no-table-indentation: true - Rule to disallow indentation of tables. Enabled.

  'lint-no-tabs': true
  # lint-no-tabs: true - Rule to disallow tabs for indentation (enforce spaces). Enabled.

  'lint-no-undefined-references': false
  # lint-no-undefined-references: false - Rule to check for undefined link or image references. Can be slow, disabled here.

  'lint-no-unused-definitions': true
  # lint-no-unused-definitions: true - Rule to disallow unused link or image definitions. Enabled.

  # "lint-no-url-trailing-slash": false # Rule to disallow trailing slashes in URLs. Disabled in the example.

  'lint-ordered-list-marker-style': '.'
  # lint-ordered-list-marker-style: "." - Rule to enforce period (.) as the marker for ordered lists (e.g., 1.).

  'lint-ordered-list-marker-value': ordered
  # lint-ordered-list-marker-value: ordered - Rule to enforce ordered list item values to be in order (1, 2, 3...). 'ordered' is used.

  'lint-rule-style': '---'
  # lint-rule-style: "---" - Rule to enforce '---' for thematic breaks (horizontal rules).

  'lint-strong-marker': '*'
  # lint-strong-marker: "*" - Rule to enforce asterisk (*) as the strong emphasis marker (e.g., **bold**).

  'lint-table-cell-padding': padded
  # lint-table-cell-padding: padded - Rule to enforce padded table cells (with spaces around content). 'padded' is used.

  'lint-table-pipe-alignment': true
  # lint-table-pipe-alignment: true - Rule to enforce consistent alignment of table pipes. Enabled.

  'lint-table-pipes': true
  # lint-table-pipes: true - Rule to enforce the presence of pipes in tables (for all table rows). Enabled.

  'lint-unordered-list-marker-style': '-'
  # lint-unordered-list-marker-style: "-" - Rule to enforce hyphen (-) as the marker for unordered lists (e.g., - list item).

  textr:
    # remark-textr - Plugin to apply typographic enhancements using the Textr library.
    #              See: https://github.com/remarkjs/remark-textr and https://github.com/shuvalov-anton/textr
    options:
      locale: en-us
      # locale: en-us -  Specifies the locale for typographic rules (English - US).
      plugins:
        - typographic-apostrophes
        # typographic-apostrophes - Plugin from Textr to improve apostrophe typography.
        - typographic-apostrophes-for-possessive-plurals
        # typographic-apostrophes-for-possessive-plurals - Textr plugin for possessive plural apostrophes.
        # - typographic-arrows # Typographic arrows plugin - commented out in the example.
        - typographic-colon
        # typographic-colon - Textr plugin for colon typography.
        - typographic-copyright
        # typographic-copyright - Textr plugin for copyright symbol typography.
        - typographic-ellipses
        # typographic-ellipses - Textr plugin for ellipses (...) typography.
        # - typographic-em-dashes # Typographic em-dashes plugin - commented out in the example.
        - typographic-en-dashes
        # typographic-en-dashes - Textr plugin for en-dashes typography.
        - typographic-exclamation-mark
        # typographic-exclamation-mark - Textr plugin for exclamation mark typography.
        - typographic-guillemets
        # typographic-guillemets - Textr plugin for guillemets (« ») typography.
        - typographic-math-symbols
        # typographic-math-symbols - Textr plugin for math symbol typography.
        - typographic-percent
        # typographic-percent - Textr plugin for percent sign typography.
        - typographic-permille
        # typographic-permille - Textr plugin for permille (‰) typography.
        - typographic-question-mark
        # typographic-question-mark - Textr plugin for question mark typography.
        - typographic-quotes
        # typographic-quotes - Textr plugin for smart quote typography.
        - typographic-semicolon
        # typographic-semicolon - Textr plugin for semicolon typography.
        # - typographic-single-spaces # Typographic single spaces plugin - commented out in the example.
        - typographic-trademark
        # typographic-trademark - Textr plugin for trademark symbol typography.

settings:
  # Settings section configures remark-stringify, which controls how Markdown syntax tree is serialized back to Markdown text.
  # See: https://github.com/remarkjs/remark-stringify#options

  bullet: '-'
  # bullet: "-" -  Sets the bullet marker for unordered lists to hyphen '-'.

  closeAtx: false
  # closeAtx: false -  Determines whether ATX headings (e.g., ## Heading) should be closed with ' #'. Set to false.

  commonmark: false
  # commonmark: false -  Enables CommonMark mode. Set to false to allow GFM and other extensions.

  emphasis: '_'
  # emphasis: "_" -  Sets the marker for emphasis (italics) to underscore '_'.

  entities: false
  # entities: false -  Determines whether to use HTML entities for potentially unsafe characters. Set to false.

  fence: '`'
  # fence: "`" -  Sets the fence marker for code blocks to backtick '`'.

  fences: true
  # fences: true -  Enables fenced code blocks (using ``` or ~~~). Set to true.

  footnotes: true
  # footnotes: true - Enables footnote syntax. Set to true.

  gfm: true
  # gfm: true -  Enables GitHub Flavored Markdown (GFM) extensions like tables, task lists, autolinks. Set to true.

  incrementListMarker: true
  # incrementListMarker: true -  Enables incrementing list markers in ordered lists (1, 2, 3...). Set to true.

  listItemIndent: '1'
  # listItemIndent: "1" -  Sets the indent for list items to 1 space.

  looseTable: false
  # looseTable: false -  Determines whether to allow loose tables (more whitespace). Set to false.

  paddedTable: true
  # paddedTable: true -  Determines whether tables should be padded with spaces for better readability. Set to true.

  pedantic: false
  # pedantic: false -  Enables pedantic mode, enforcing stricter Markdown parsing. Set to false for more flexibility.

  rule: '-'
  # rule: "-" -  Sets the character used for thematic breaks (horizontal rules) to hyphen '-'.

  ruleRepetition: 3
  # ruleRepetition: 3 -  Sets the number of repetitions for thematic break markers (---).

  ruleSpaces: false
  # ruleSpaces: false -  Determines whether to allow spaces between thematic break markers. Set to false.

  setext: false
  # setext: false -  Disables Setext heading style (e.g., Heading =====). Set to false, preferring ATX headings.

  spacedTable: true
  # spacedTable: true -  Determines whether tables should be spaced. Set to true for better readability.

  strong: '*'
  # strong: "*" -  Sets the marker for strong emphasis (bold) to asterisk '*'.

  yaml: true
  # yaml: true -  Enables YAML frontmatter parsing. Set to true to support YAML frontmatter.
````

Yes, you can have a global configuration for VSCode settings. The global settings file
`settings.json` for VSCode on macOS is typically located at:

```
~/Library/Application Support/Code/User/settings.json
```

For Cursor editor, which is based on VSCode, it is likely that the global settings file is located
at the path you mentioned:

```
~/Library/Application Support/Cursor/User/settings.json
```

You can verify this by opening the settings in Cursor (Cmd + , or Cursor > Settings) and then
opening the settings JSON file using the "Open Settings (JSON)" command in the Command Palette
(Cmd+Shift+P). The location will be shown at the top of the editor.

Regarding the `remarkrc.yml` file, please find below an exquisite, annotated, and well-organized
example based on your provided information:

```yaml
# remarkrc.yml
# Configuration file for unifiedjs.vscode-remark VSCode extension.
# ... (rest of the yml content from above)
```

This `remarkrc.yml` file provides a comprehensive configuration for remark, including various
plugins and detailed linting rules, along with typographic enhancements and markdown serialization
settings. You can place this file in the root of your project or in a parent directory to apply
these settings to your Markdown files when using the `unifiedjs.vscode-remark` VSCode extension.

## Analysis of `unifiedjs.vscode-remark`

This VSCode extension integrates the remark Markdown processor into the editor, providing linting
and formatting capabilities. It leverages the Language Server Protocol (LSP) through
`remark-language-server` to communicate with the remark engine.

Here's a breakdown:

- **Functionality:**
  - **Linting:** Checks Markdown files for style and consistency issues based on remark plugins
    (like `remark-lint`). Problems are displayed in the VSCode "Problems" panel.
  - **Formatting:** Formats Markdown files according to the configured remark plugins (typically
    through a `.remarkrc` file). This can be triggered manually or on save.
- **Configuration:**
  - Uses the same configuration files as `remark-cli` (`.remarkrc`, `.remarkrc.js`,
    `.remarkrc.json`, `.remarkrc.yaml`, `.remarkrc.yml`, or `package.json`). This ensures
    consistency between editor integration and command-line usage.
  - Supports a `remark.requireConfig` setting (default: `false`). If set to `true`, the extension
    will _only_ activate if a remark configuration file is found in the workspace. This is important
    for projects that _must_ adhere to a specific style guide.
- **Activation:**
  - Activates when a Markdown file (`onLanguage:markdown`) is opened.
  - Starts a `LanguageClient` that communicates with the `remark-language-server` (bundled in the
    `out` directory).
  - Uses `TransportKind.ipc` for communication between the extension and the language server.
  - Watches for changes to remark configuration files (`.remarkignore`, `.remarkrc.*`,
    `package.json`) to reload the configuration.
- **Dependencies:**
  - `vscode`: VSCode API.
  - `vscode-languageclient`: For implementing the Language Server Protocol client.
  - `remark-language-server`: The server-side component that handles the remark processing.
  - `remark-cli`: Used in tests and likely as a reference point for configuration file discovery.
  - `remark-preset-wooorm`: A popular remark preset for linting, likely used as a default or example
    configuration.
  - `esbuild`: Bundler for the extension, creating the output in the `out` folder.
  - `typescript`: For type checking.
  - `xo` and `prettier`: for linting/formatting the extension's sourcecode.
- **Test:** A simple test is there to check the format Document.

## Global Configuration in VSCode

Yes, you can provide global defaults for remark within VSCode's user settings (`settings.json`).
However, it's crucial to understand how this interacts with project-specific configuration.

**How it works:**

1.  **Project-Specific Configuration (Priority):** If a `.remarkrc` file (or any of the other
    supported configuration file names) exists in your project's workspace, the extension will
    _always_ prioritize that configuration. This is the recommended approach for consistent styling
    within a project.

2.  **Global User Settings (Fallback):** If _no_ project-specific configuration is found, _and_
    `remark.requireConfig` is `false` (the default), _then_ the extension will look for remark
    configuration within your VSCode user settings.

**How to set global defaults in `settings.json`:**

You can add a `remarkConfig` object to your global `settings.json` file (located at
`~/Library/Application Support/Code/User/settings.json` or
`~/Library/Application Support/Cursor/User/settings.json` depending on the editor you are using. You
can find it with <kbd>Ctrl</kbd> + <kbd>,</kbd> or <kbd>Cmd</kbd> + <kbd>,</kbd>). This object
should follow the same structure as a `.remarkrc` file.

```json
{
  "remark.requireConfig": false, // Important: Make sure this is false (or absent) to use global settings
  "remarkConfig": {
    "settings": {
      "bullet": "-",
      "emphasis": "_",
      "strong": "*",
      "listItemIndent": "one"
    },
    "plugins": [
      "remark-preset-lint-consistent",
      "remark-preset-lint-recommended"
      // Add other plugins here as needed
    ]
  }
}
```

**Important Considerations:**

- **`remark.requireConfig`:** Remember, if `remark.requireConfig` is `true`, the global settings
  will be _ignored_ if no project-specific configuration is found.
- **Plugin Installation:** Even with global settings, you still need to ensure that any remark
  plugins you reference (like `remark-preset-lint-consistent`) are installed in a location where the
  language server can find them. This typically means either:
  - Installing them globally with `npm install -g remark-preset-lint-consistent`.
  - Having them listed as `devDependencies` in a `package.json` file within a parent directory of
    your Markdown files. The extension will search upwards for a `package.json`.
- **Overrides:** Project-specific `.remarkrc` files will _always_ override the global `remarkConfig`
  settings.
- **`remark-cli` Consistency:** If you use `remark-cli` on the command line, be aware that it will
  _not_ use your VSCode `settings.json`. For consistent behavior, you _must_ use a `.remarkrc` file,
  even if you also set global defaults in VSCode.

## Exquisite, Annotated `remarkrc.yml`

Here's a well-organized, annotated `remarkrc.yml` file, combining best practices and addressing your
requirements:

```yaml
# --- General Settings ---

# Determines how remark serializes the Markdown.
settings:
  # List item bullet character.
  bullet: '-'

  # Character to use around emphasized text.
  emphasis: '_'

  # Character to use around strong text.
  strong: '*'

  # How to indent the content of list items.  "one" is generally preferred.
  listItemIndent: 'one'

  # Whether to use ATX-style headings (# Heading) or Setext-style (Heading\n---).
  setext: false

  # Whether to close ATX-style headings with # characters.
  closeAtx: false

  # Character to use for fences (code blocks).
  fence: '`'

  # Always use fences for code blocks, even if they could be indented.
  fences: true

  # Whether to use footnotes ([^1]) or inline footnotes.
  footnotes: true

  # Whether to use GFM (GitHub Flavored Markdown) extensions.
  gfm: true

  # Whether to allow a blank line between a list item and the next block.
  looseTable: false

  # Whether to pad table cells with spaces.
  paddedTable: true

  # Character to use for horizontal rules.
  rule: '-'

  # Number of `-` characters to use for horizontal rules.
  ruleRepetition: 3

  # Whether to add spaces around horizontal rules.
  ruleSpaces: false

  # Whether to pad table cells with exactly one space (true) or at least one (padded).
  spacedTable: true

  # Whether to increment list item markers (1, 2, 3) or use the same marker (1, 1, 1).
  incrementListMarker: true

  # Whether to use CommonMark mode (more strict).
  commonmark: false

  # Whether to use "pedantic" mode (even more strict).
  pedantic: false

# --- Plugins ---

# remark-frontmatter: Adds support for YAML frontmatter.
# remark-gfm: Enables GitHub Flavored Markdown.
# remark-validate-links: Checks for broken links (internal and external).
# remark-heading-gap: Controls spacing around headings.
# remark-inline-links: Converts reference-style links to inline links.
# remark-squeeze-paragraphs: Removes empty paragraphs.
# remark-yaml-config: Loads configuration from YAML files (like this one!).
# remark-textr: Applies typographic improvements.

plugins:
  - remark-preset-lint-consistent # Enforces consistent Markdown style.
  - remark-preset-lint-recommended # Recommended linting rules.
  - remark-preset-lint-markdown-style-guide # Follows a common style guide.

  - remark-frontmatter

  # GitHub Flavored Markdown support (tables, strikethrough, etc.).
  - remark-gfm

  # Link validation (check for broken links).
  - remark-validate-links:
      repository: false # Disable repo check; assume local/web links are valid.

  # Control spacing around headings.
  - remark-heading-gap:
      1: # Top-level headings (H1)
        before: "\n\n" # Two blank lines before.
        after: "\n" # One blank line after.
      2: # Second-level headings (H2)
        before: "\n" # One blank line before.
        after: "\n" # One blank line after.

  # Convert reference-style links/images to inline.
  - remark-inline-links

  # Remove unnecessary empty paragraphs.
  - remark-squeeze-paragraphs

  # Allows configuring remark with YAML (this file!).
  - remark-yaml-config

  # Typographic improvements (smart quotes, dashes, etc.).
  - remark-textr:
      options:
        locale: 'en-us' # Specify the locale for language-specific rules.
      plugins:
        - typographic-apostrophes
        - typographic-apostrophes-for-possessive-plurals
        - typographic-ellipses
        - typographic-en-dashes
        - typographic-quotes

  # Github Blockquote
  - remark-github-blockquote-alert

  # Table of Content
  - remark-toc:
      heading: '[contents|toc]'
      tight: true

  # Directives
  - remark-directive
  - remark-directive-rehype

# --- Linting Rules (Overrides and Additions) ---

# The lint rules from the presets can be overridden here.
# See: https://github.com/remarkjs/remark-lint

lint:
  # Maximum line length (120 characters).
  maximum-line-length: 120

  # Don't allow HTML in Markdown.
  no-html: false #Turned off to allow directives (":::")

  # Ensure there's a blank line after the final definition.
  final-definition: true

  # Ensure there's a final newline at the end of the file.
  final-newline: true

  # Require ATX-style headings (# Heading).
  heading-style: atx

  # Don't allow shortcut reference links.
  no-shortcut-reference-link: false
  no-shortcut-reference-image: false

  # Don't allow literal URLs without angle brackets.
  no-literal-urls: false

  # No undefined references
  no-undefined-references: false

  # No unused definitions
  no-unused-definitions: true

  # No consecutive blank lines
  no-consecutive-blank-lines: true
```

Key improvements and explanations in this `remarkrc.yml`:

- **Clear Organization:** Uses comments to separate sections (General Settings, Plugins, Linting
  Rules). This makes it much easier to understand the purpose of each part.
- **Comprehensive Settings:** Includes a wide range of `settings` to control how remark serializes
  Markdown. This covers all the commonly customized options.
- **Plugin Presets:** Uses `remark-preset-lint-consistent`, `remark-preset-lint-recommended`, and
  `remark-preset-lint-markdown-style-guide`. These presets provide a solid foundation for linting
  and style enforcement. Using presets reduces the need to specify many individual rules.
- **Essential Plugins:** Includes `remark-frontmatter`, `remark-gfm`, `remark-validate-links`,
  `remark-heading-gap`, `remark-inline-links`, `remark-squeeze-paragraphs`, `remark-yaml-config`,
  and `remark-textr`. These cover common needs like frontmatter support, GitHub Flavored Markdown,
  link checking, and typographic improvements.
- **`remark-validate-links` Configuration:** Sets `repository: false`. This is crucial because,
  without a specific repository configured, `remark-validate-links` can be overly aggressive and
  cause false positives. By setting it to `false`, we're essentially telling the plugin to only
  check for _really_ broken links (like malformed URLs) and not to try to resolve relative links
  within a repository.
- **`remark-heading-gap` Configuration:** Provides explicit control over the spacing before and
  after headings, making the output more readable.
- **`remark-textr` Configuration:** Includes the `locale` option for language-specific typographic
  rules (e.g., different quotation marks in different languages). Also lists specific `textr`
  plugins for fine-grained control.
- **Lint Rule Overrides:** Shows how to override specific linting rules from the presets. The
  `maximum-line-length` and `no-html` rules are good examples.
- **Comments:** Includes comments _throughout_ the file to explain _why_ each setting or plugin is
  used. This is essential for maintainability.
- **Consistent Style:** The YAML itself is formatted consistently, making it easy to read and
  modify.
- **Directives:** Include the plugins for handling directives.
- **ToC:** Add a table of contents by simply adding `[toc]` or `[contents]`

This `remarkrc.yml` provides a robust and well-documented configuration for remark, suitable for use
with the VSCode extension and `remark-cli`. It covers a wide range of common needs and provides a
good starting point for customization. It prioritizes readability, maintainability, and consistency.
Remember to install the necessary plugins using `npm install --save-dev` or `npm install -g`.

Based on the search results and repository analysis, I'll help you understand the VSCode Extension
unifiedjs.vscode-remark and create a well-organized remarkrc.yml configuration file.

### Global Configuration Location

Yes, you can have a global config for remark in your VSCode settings. For macOS, the location would
be:

```
~/Library/Application Support/Code/User/settings.json
```

Add the following to enable remark as the default markdown formatter:

```json
{
  "[markdown]": {
    "editor.defaultFormatter": "unifiedjs.vscode-remark",
    "editor.formatOnSave": true
  }
}
```

### Annotated remarkrc.yml Configuration

Here's a comprehensive, well-organized remarkrc.yml file with comments:

```yaml
# Output configuration
output: true

# Core plugins configuration
plugins:
  # Handle frontmatter in markdown files
  frontmatter: {}

  # Support GitHub Flavored Markdown features
  gfm: true

  # Support hard line breaks without spaces
  breaks: true

  # Table of contents generation
  toc:
    tight: true
    maxDepth: 3
    heading: 'Contents'

  # Markdown formatting plugins
  lint:
    # List related rules
    alphabetize-lists: false
    list-item-bullet-indent: false
    list-item-content-indent: true
    list-item-indent: space
    list-item-spacing:
      checkBlanks: true

    # Heading related rules
    heading-increment: true
    heading-style: atx
    maximum-heading-length: 300
    no-duplicate-headings: true

    # Code block rules
    code-block-style: fenced
    fenced-code-marker: '`'
    fenced-code-flag:
      allowEmpty: true

    # Link related rules
    link-title-style: consistent
    no-undefined-references: false
    no-unused-definitions: true

    # General formatting rules
    emphasis-marker: '_'
    strong-marker: '*'
    final-newline: true
    no-consecutive-blank-lines: true
    no-tabs: true

  # Typography enhancements
  textr:
    options:
      locale: en-us
    plugins:
      - typographic-apostrophes
      - typographic-quotes
      - typographic-em-dashes
      - typographic-en-dashes
      - typographic-ellipses
      - typographic-single-spaces
      - typographic-math-symbols

  # Image handling
  images:
    # Enable image optimization
    optimize: true
    # Handle relative paths
    resolveRelative: true

  # Extended table support
  extended-table: {}

  # Definition list support
  definition-list: {}

# Markdown parsing settings
settings:
  # List markers
  bullet: '-'
  ordered: '.'

  # Code fence settings
  fence: '`'
  fences: true

  # General formatting
  incrementListMarker: true
  listItemIndent: '1'

  # Table formatting
  paddedTable: true
  spacedTable: true

  # Special features
  footnotes: true
  yaml: true

  # Emphasis markers
  emphasis: '_'
  strong: '*'
```

### Key Features Explained

1. **Core Configuration**:

   - Enables frontmatter support
   - Configures GitHub Flavored Markdown features
   - Sets up table of contents generation

2. **Formatting Rules**:

   - Consistent list formatting
   - Heading structure rules
   - Code block styling
   - Link validation and management

3. **Typography Enhancement**:

   - Locale-based typography rules
   - Smart punctuation conversion
   - Mathematical symbol handling

4. **Extended Features**:
   - Table extensions
   - Definition list support
   - Image optimization
   - Footnote support

This configuration provides a robust setup for markdown processing while maintaining readability and
consistency. You can adjust the settings based on your specific needs while keeping the structure
organized.
