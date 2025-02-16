TODO: Analyze the VSCode Extension unifiedjs.vscode-remark

Can I have a global config somewhere in the VSCode JSON settings like ~/Library/Application
Support/Cursor/User/settings.json ?

Other than that, based on all the examples, craft an exquisite, annotated (with comments),
well-organized remarkrc.yml file that will be used by the VSCode Extension unifiedjs.vscode-remark.

## Recent plugins info from https://github.com/remarkjs/remark/blob/main/doc/plugins.md

![remark][file-logo]

# Plugins

**remark** is a tool that transforms markdown with plugins. See [the monorepo readme][github-remark]
for info on what the remark ecosystem is. This page lists existing plugins.

## Contents

- [List of plugins](#list-of-plugins)
- [List of utilities](#list-of-utilities)
- [Use plugins](#use-plugins)
- [Create plugins](#create-plugins)

## List of plugins

<a id="list-of-presets"></a>

For the most awesome projects in the ecosystem, see
[`remarkjs/awesome-remark`][github-remark-awesome-remark]. More plugins can be found on GitHub
tagged with the [`remark-plugin` topic][github-topic-remark-plugin].

> 👉 **Note**: some plugins don’t work with recent versions of remark due to changes in its
> underlying parser (micromark). Plugins that are up to date or unaffected are marked with `🟢`
> while plugins that are **currently broken** are marked with `⚠️`.

> 💡 **Tip**: remark plugins work with markdown and **rehype** plugins work with HTML. See [_§ List
> of plugins_ in `rehypejs/rehype`][github-rehype-plugins] for more plugins.

<!--lint disable media-style-->

The list of plugins:

- [`remark-a11y-emoji`](https://github.com/florianeckerstorfer/remark-a11y-emoji) — accessible emoji
- ⚠️
  [`remark-abbr`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-abbr#readme)
  — new syntax for abbreviations (new node type, rehype compatible)
- ⚠️ [`remark-admonitions`](https://github.com/elviswolcott/remark-admonitions) — new syntax for
  admonitions (👉 **note**: [`remark-directive`][github-remark-directive] is similar and up to date)
- ⚠️
  [`remark-align`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-align#readme)
  — new syntax to align text or blocks (new node types, rehype compatible)
- 🟢 [`remark-api`](https://github.com/wooorm/remark-api) — generate an API section
- ⚠️ [`remark-attr`](https://github.com/arobase-che/remark-attr) — new syntax to add attributes to
  markdown
- 🟢 [`remark-behead`](https://github.com/mrzmmr/remark-behead) — increase or decrease heading depth
- 🟢 [`remark-breaks`](https://github.com/remarkjs/remark-breaks) – hard breaks w/o needing spaces
  (like on issues)
- 🟢 [`remark-capitalize`](https://github.com/zeit/remark-capitalize) – transform all titles w/
  [`title.sh`](https://github.com/zeit/title)
- 🟢
  [`remark-capitalize-headings`](https://github.com/Xunnamius/unified-utils/blob/main/packages/remark-capitalize-headings)
  – selectively capitalize headings (👉 **note**: alternative to
  [`remark-capitalize`](https://github.com/zeit/remark-capitalize))
- 🟢 [`remark-cite`](https://github.com/benrbray/remark-cite) – new syntax for Pandoc-style
  citations
- 🟢 [`remark-cloudinary-docusaurus`](https://github.com/johnnyreilly/remark-cloudinary-docusaurus)
  – allows Docusaurus to use Cloudinary to serve optimised images
- 🟢 [`remark-code-blocks`](https://github.com/mrzmmr/remark-code-blocks) — select and store code
  blocks
- 🟢 [`remark-code-extra`](https://github.com/samlanning/remark-code-extra) — add to or transform
  the HTML output of code blocks (rehype compatible)
- 🟢 [`remark-code-frontmatter`](https://github.com/samlanning/remark-code-frontmatter) — extract
  frontmatter from code blocks
- 🟢 [`remark-code-import`](https://github.com/kevin940726/remark-code-import) — populate code
  blocks from files
- 🟢 [`remark-code-screenshot`](https://github.com/Swizec/remark-code-screenshot) – turn code blocks
  into `carbon.now.sh` screenshots
- 🟢 [`remark-code-title`](https://github.com/kevinzunigacuellar/remark-code-title) — add titles to
  code blocks
- 🟢 [`remark-codesandbox`](https://github.com/kevin940726/remark-codesandbox) – create CodeSandbox
  from code blocks
- 🟢 [`remark-collapse`](https://github.com/Rokt33r/remark-collapse) — make a section collapsible
- 🟢 [`remark-comment-config`](https://github.com/remarkjs/remark-comment-config) — configure remark
  w/ comments
- ⚠️
  [`remark-comments`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-comments#readme)
  — new syntax to ignore things
- ⚠️ [`remark-container`](https://github.com/zWingz/remark-container) — new syntax for containers
  (👉 **note**: [`remark-directive`][github-remark-directive] is similar and up to date)
- ⚠️ [`remark-containers`](https://github.com/Nevenall/remark-containers) — new syntax for
  containers (👉 **note**: [`remark-directive`][github-remark-directive] is similar and up to date)
- 🟢 [`remark-contributors`](https://github.com/remarkjs/remark-contributors) — add a table of
  contributors
- 🟢 [`remark-copy-linked-files`](https://github.com/sergioramos/remark-copy-linked-files) — find
  and copy files linked files to a destination directory
- 🟢 [`remark-corebc`](https://github.com/bchainhub/remark-corebc) — transforms Core Blockchain
  notations into markdown links
- 🟢 [`remark-corepass`](https://github.com/bchainhub/remark-corepass) — transform CorePass
  notations into markdown links
- ⚠️
  [`remark-custom-blocks`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-custom-blocks#readme)
  — new syntax for custom blocks (new node types, rehype compatible) (👉 **note**:
  [`remark-directive`][github-remark-directive] is similar and up to date)
- 🟢 [`remark-custom-header-id`](https://github.com/sindresorhus/remark-custom-header-id) — add
  custom ID attribute to headers (`{#some-id}`)
- 🟢 [`remark-definition-list`](https://github.com/wataru-chocola/remark-definition-list) — support
  definition lists
- 🟢 [`remark-defsplit`](https://github.com/remarkjs/remark-defsplit) — change links and images to
  references w/ separate definitions
- ⚠️
  [`remark-disable-tokenizers`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-disable-tokenizers#readme)
  — turn some or all remark’s tokenizers on or off
- 🟢 [`remark-directive`](https://github.com/remarkjs/remark-directive) — new syntax for directives
  (generic extensions)
- 🟢 [`remark-directive-rehype`](https://github.com/IGassmann/remark-directive-rehype) — turn
  [directives][github-remark-directive] into HTML custom elements (rehype compatible)
- 🟢 [`remark-directive-sugar`](https://github.com/lin-stephanie/remark-directive-sugar) —
  predefined directives for customizable badges, links, video embeds, and more
- 🟢 [`remark-docx`](https://github.com/inokawa/remark-docx) — compile markdown to docx
- 🟢 [`remark-dropcap`](https://github.com/brev/remark-dropcap) — fancy and accessible drop caps
- 🟢 [`remark-embed-images`](https://github.com/remarkjs/remark-embed-images) — embed local images
  as base64-encoded data URIs
- 🟢 [`remark-emoji`](https://github.com/rhysd/remark-emoji) — transform Gemoji short-codes to emoji
- 🟢 [`remark-extended-table`](https://github.com/wataru-chocola/remark-extended-table) — extended
  table syntax allowing colspan / rowspan
- 🟢 [`remark-extract-frontmatter`](https://github.com/mrzmmr/remark-extract-frontmatter) — store
  front matter in vfiles
- 🟢 [`remark-fediverse-user`](https://github.com/bchainhub/remark-fediverse-user) — transform
  Fediverse user notations into markdown links
- 🟢 [`remark-first-heading`](https://github.com/laat/remark-first-heading) — change the first
  heading in a document
- 🟢
  [`remark-fix-guillemets`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-fix-guillemets#readme)
  — support ASCII guillements (`<<`, `>>`) mapping them to HTML
- 🟢 [`remark-flexible-code-titles`](https://github.com/ipikuka/remark-flexible-code-titles) — add
  titles or/and containers for code blocks with customizable attributes
- 🟢 [`remark-flexible-containers`](https://github.com/ipikuka/remark-flexible-containers) — add
  custom/flexible containers with customizable properties
- 🟢 [`remark-flexible-markers`](https://github.com/ipikuka/remark-flexible-markers) — add
  custom/flexible mark element with customizable properties
- 🟢 [`remark-flexible-paragraphs`](https://github.com/ipikuka/remark-flexible-paragraphs) — add
  custom/flexible paragraphs with customizable properties
- 🟢 [`remark-flexible-toc`](https://github.com/ipikuka/remark-flexible-toc) — expose the table of
  contents (toc) via Vfile.data or an option reference
- 🟢 [`remark-footnotes-extra`](https://github.com/miaobuao/remark-footnotes-extra) — add footnotes
  via short syntax
- 🟢 [`remark-frontmatter`](https://github.com/remarkjs/remark-frontmatter) – support frontmatter
  (yaml, toml, and more)
- 🟢 [`remark-gemoji`](https://github.com/remarkjs/remark-gemoji) — better support for Gemoji
  shortcodes
- ⚠️ [`remark-generic-extensions`](https://github.com/medfreeman/remark-generic-extensions) — new
  syntax for the CommonMark generic directive extension (👉 **note**:
  [`remark-directive`][github-remark-directive] is similar and up to date)
- 🟢 [`remark-gfm`](https://github.com/remarkjs/remark-gfm) — support GFM (autolink literals,
  footnotes, strikethrough, tables, tasklists)
- 🟢 [`remark-git-contributors`](https://github.com/remarkjs/remark-git-contributors) — add a table
  of contributors based on Git history, options, and more
- 🟢 [`remark-github`](https://github.com/remarkjs/remark-github) — autolink references to commits,
  issues, pull-requests, and users
- 🟢
  [`remark-github-admonitions-to-directives`](https://github.com/incentro-dc/remark-github-admonitions-to-directives)
  — convert GitHub’s blockquote-based admonitions syntax to directives syntax
- 🟢
  [`remark-github-beta-blockquote-admonitions`](https://github.com/myl7/remark-github-beta-blockquote-admonitions)
  — [GitHub beta blockquote-based admonitions](https://github.com/github/feedback/discussions/16925)
- 🟢
  [`remark-github-blockquote-alert`](https://github.com/jaywcjlove/remark-github-blockquote-alert) —
  remark plugin to add support for
  [GitHub Alert](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#alerts)
- ⚠️
  [`remark-grid-tables`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-grid-tables#readme)
  — new syntax to describe tables (rehype compatible)
- 🟢 [`@adobe/remark-grid-tables`](https://github.com/adobe/remark-gridtables) — pandoc compatible
  grid-table syntax
- 🟢 [`remark-heading-id`](https://github.com/imcuttle/remark-heading-id) — custom heading id
  support `{#custom-id}`
- 🟢 [`remark-heading-gap`](https://github.com/remarkjs/remark-heading-gap) — serialize w/ more
  blank lines between headings
- 🟢 [`@vcarl/remark-headings`](https://github.com/vcarl/remark-headings) — extract a list of
  headings as data
- 🟢 [`remark-hexo`](https://github.com/bennycode/remark-hexo) — renders
  [Hexo tags](https://hexo.io/docs/tag-plugins)
- 🟢 [`remark-highlight.js`](https://github.com/remarkjs/remark-highlight.js) — highlight code
  blocks w/ [`highlight.js`](https://github.com/isagalaev/highlight.js) (rehype compatible)
- 🟢 [`remark-hint`](https://github.com/sergioramos/remark-hint) — add hints/tips/warnings to
  markdown
- 🟢 [`remark-html`](https://github.com/remarkjs/remark-html) — serialize markdown as HTML
- ⚠️
  [`remark-iframes`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-iframes#readme)
  — new syntax to create iframes (new node type, rehype compatible)
- 🟢 [`remark-ignore`](https://github.com/Xunnamius/unified-utils/blob/main/packages/remark-ignore)
  — use comments to exclude nodes from transformation
- 🟢 [`remark-images`](https://github.com/remarkjs/remark-images) — add an improved image syntax
- 🟢 [`remark-img-links`](https://github.com/Pondorasti/remark-img-links) — prefix relative image
  paths with an absolute URL
- 🟢 [`remark-inline-links`](https://github.com/remarkjs/remark-inline-links) — change references
  and definitions to links and images
- 🟢 [`remark-ins`](https://github.com/ipikuka/remark-ins) — add ins element for inserted texts
  opposite to deleted texts
- 🟢 [`remark-join-cjk-lines`](https://github.com/purefun/remark-join-cjk-lines) — remove extra
  space between CJK Characters.
- ⚠️ [`remark-kbd`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-kbd#readme)
  — new syntax for keyboard keys (new node type, rehype compatible)
- ⚠️ [`remark-kbd-plus`](https://github.com/twardoch/remark-kbd-plus) — new syntax for keyboard keys
  w/ plusses (new node type, rehype compatible)
- 🟢 [`remark-license`](https://github.com/remarkjs/remark-license) — add a license section
- 🟢 [`remark-link-rewrite`](https://github.com/rjanjic/remark-link-rewrite) — customize link URLs
  dynamically
- 🟢 [`remark-linkify-regex`](https://gitlab.com/staltz/remark-linkify-regex) — change text matching
  a regex to links
- 🟢 [`remark-lint`](https://github.com/remarkjs/remark-lint) — check markdown code style
- 🟢 [`remark-man`](https://github.com/remarkjs/remark-man) — serialize markdown as man pages (roff)
- 🟢 [`remark-math`](https://github.com/remarkjs/remark-math) — new syntax for math (new node types,
  rehype compatible)
- 🟢 [`remark-mdx`](https://github.com/mdx-js/mdx/tree/main/packages/remark-mdx) — support MDX (JSX,
  expressions, ESM)
- 🟢 [`remark-mentions`](https://github.com/FinnRG/remark-mentions) — replace @ mentions with links
- 🟢 [`remark-mermaidjs`](https://github.com/remcohaszing/remark-mermaidjs) — transform mermaid code
  blocks into inline SVGs
- 🟢 [`remark-message-control`](https://github.com/remarkjs/remark-message-control) — turn some or
  all messages on or off
- 🟢 [`remark-normalize-headings`](https://github.com/remarkjs/remark-normalize-headings) — make
  sure at most one top-level heading exists
- 🟢
  [`remark-numbered-footnote-labels`](https://github.com/jackfletch/remark-numbered-footnote-labels)
  — label footnotes w/ numbers
- 🟢 [`@agentofuser/remark-oembed`](https://github.com/agentofuser/remark-oembed) — transform URLs
  for youtube, twitter, etc. embeds
- 🟢 [`remark-oembed`](https://github.com/sergioramos/remark-oembed) — transform URLs surrounded by
  newlines into _asynchronously_ loading embeds
- 🟢 [`remark-package-dependencies`](https://github.com/unlight/remark-package-dependencies) —
  inject your dependencies
- ⚠️ [`remark-parse-yaml`](https://github.com/landakram/remark-parse-yaml) — parse YAML nodes and
  expose their value as `parsedValue`
- 🟢 [`remark-pdf`](https://github.com/inokawa/remark-pdf) — compile markdown to pdf
- ⚠️
  [`remark-ping`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-ping#readme)
  — new syntax for mentions w/ configurable existence check (new node type, rehype compatible)
- 🟢 [`remark-prepend-url`](https://github.com/alxjpzmn/remark-prepend-url) — prepend an absolute
  url to relative links
- 🟢 [`remark-prettier`](https://github.com/remcohaszing/remark-prettier) — check and format
  markdown using Prettier
- 🟢 [`remark-prism`](https://github.com/sergioramos/remark-prism) — highlight code blocks w/
  [Prism](https://prismjs.com/) (supporting most Prism plugins)
- 🟢
  [`@handlewithcare/remark-prosemirror`](https://github.com/handlewithcarecollective/remark-prosemirror)
  — compile markdown to [ProseMirror](https://prosemirror.net/) documents
- ⚠️ [`remark-redact`](https://github.com/seafoam6/remark-redact) — new syntax to conceal text
  matching a regex
- 🟢 [`remark-redactable`](https://github.com/code-dot-org/remark-redactable) — write plugins to
  redact content from a markdown document, then restore it later
- 🟢 [`remark-reference-links`](https://github.com/remarkjs/remark-reference-links) — transform
  links and images into references and definitions
- 🟢 [`remark-rehype`](https://github.com/remarkjs/remark-rehype) — transform to
  [rehype](https://github.com/rehypejs/rehype)
- 🟢 [`remark-relative-links`](https://github.com/zslabs/remark-relative-links) — change absolute
  URLs to relative ones
- 🟢 [`remark-remove-comments`](https://github.com/alvinometric/remark-remove-comments) — remove
  HTML comments from the processed output
- 🟢
  [`remark-remove-unused-definitions`](https://github.com/Xunnamius/unified-utils/blob/main/packages/remark-remove-unused-definitions)
  — remove unused reference-style link definitions
- 🟢
  [`remark-remove-url-trailing-slash`](https://github.com/Xunnamius/unified-utils/blob/main/packages/remark-remove-url-trailing-slash)
  — remove trailing slashes from the ends of all URL paths
- 🟢
  [`remark-renumber-references`](https://github.com/Xunnamius/unified-utils/blob/main/packages/remark-renumber-references)
  — renumber numeric reference-style link ids contiguously starting from 1
- 🟢 [`remark-retext`](https://github.com/remarkjs/remark-retext) — transform to
  [retext](https://github.com/retextjs/retext)
- 🟢 [`remark-ruby`](https://github.com/laysent/remark-ruby) — new syntax for ruby (furigana)
- 🟢 [`remark-sectionize`](https://github.com/jake-low/remark-sectionize) — wrap headings and
  subsequent content in section tags (new node type, rehype compatible)
- ⚠️ [`remark-shortcodes`](https://github.com/djm/remark-shortcodes) — new syntax for Wordpress- and
  Hugo-like shortcodes (new node type) (👉 **note**: [`remark-directive`][github-remark-directive]
  is similar and up to date)
- 🟢 [`remark-simple-plantuml`](https://github.com/akebifiky/remark-simple-plantuml) — turn PlantUML
  code blocks to images
- 🟢 [`remark-slate`](https://github.com/hanford/remark-slate) — compile markdown to
  [Slate nodes](https://docs.slatejs.org/concepts/02-nodes)
- 🟢 [`remark-slate-transformer`](https://github.com/inokawa/remark-slate-transformer) — compile
  markdown to [Slate nodes](https://docs.slatejs.org/concepts/02-nodes) and Slate nodes to markdown
- 🟢 [`remark-smartypants`](https://github.com/silvenon/remark-smartypants) — SmartyPants
- 🟢 [`remark-smcat`](https://github.com/shedali/remark-smcat) — state machine cat
- 🟢
  [`remark-sort-definitions`](https://github.com/Xunnamius/unified-utils/blob/main/packages/remark-sort-definitions)
  — reorder reference-style link definitions
- 🟢 [`remark-sources`](https://github.com/unlight/remark-sources) — insert source code
- 🟢 [`remark-strip-badges`](https://github.com/remarkjs/remark-strip-badges) — remove badges (such
  as `shields.io`)
- 🟢 [`remark-strip-html`](https://github.com/craftzdog/remark-strip-html) — remove HTML
- 🟢 [`remark-squeeze-paragraphs`](https://github.com/remarkjs/remark-squeeze-paragraphs) — remove
  empty paragraphs
- ⚠️
  [`remark-sub-super`](https://github.com/zestedesavoir/zmarkdown/tree/HEAD/packages/remark-sub-super)
  — new syntax for super- and subscript (new node types, rehype compatible)
- ⚠️ [`remark-terms`](https://github.com/Nevenall/remark-terms) — new customizable syntax for
  special terms and phrases
- 🟢 [`remark-textr`](https://github.com/remarkjs/remark-textr) — transform text w/
  [`Textr`](https://github.com/shuvalov-anton/textr)
- 🟢
  [`remark-tight-comments`](https://github.com/Xunnamius/unified-utils/blob/main/packages/remark-tight-comments)
  — selectively remove newlines around comments
- 🟢 [`remark-title`](https://github.com/RichardLitt/remark-title) — check and add the document
  title
- 🟢 [`remark-toc`](https://github.com/remarkjs/remark-toc) — add a table of contents
- 🟢 [`remark-torchlight`](https://github.com/torchlight-api/remark-torchlight) — syntax
  highlighting powered by [torchlight.dev](https://torchlight.dev)
- 🟢 [`remark-tree-sitter`](https://github.com/samlanning/remark-tree-sitter) — highlight code
  blocks in markdown files using [Tree-sitter](https://tree-sitter.github.io/tree-sitter/) (rehype
  compatible)
- 🟢
  [`remark-truncate-links`](https://github.com/GaiAma/Coding4GaiAma/tree/HEAD/packages/remark-truncate-links)
  — truncate/shorten urls not manually named
- 🟢 [`remark-twemoji`](https://github.com/madiodio/remark-twemoji) — turn emoji into
  [Twemoji](https://github.com/twitter/twemoji)
- 🟢 [`remark-typedoc-symbol-links`](https://github.com/kamranayub/remark-typedoc-symbol-links) —
  turn Typedoc symbol link expressions into markdown links
- 🟢 [`remark-typescript`](https://github.com/trevorblades/remark-typescript) — turn TypeScript code
  to JavaScript
- 🟢 [`remark-typograf`](https://github.com/mavrin/remark-typograf) — transform text w/
  [Typograf](https://github.com/typograf)
- 🟢 [`remark-unlink`](https://github.com/remarkjs/remark-unlink) — remove all links, references,
  and definitions
- 🟢 [`remark-unwrap-images`](https://github.com/remarkjs/remark-unwrap-images) — remove the
  wrapping paragraph for images
- 🟢 [`remark-usage`](https://github.com/remarkjs/remark-usage) — add a usage example
- 🟢 [`remark-utf8`](https://github.com/Swizec/remark-utf8) — turn bolds, italics, and code into UTF
  8 special characters
- 🟢 [`remark-validate-links`](https://github.com/remarkjs/remark-validate-links) — check links to
  headings and files
- ⚠️ [`remark-variables`](https://github.com/mrzmmr/remark-variables) — new syntax for variables
- 🟢 [`remark-vdom`](https://github.com/remarkjs/remark-vdom) — compile markdown to
  [VDOM](https://github.com/Matt-Esch/virtual-dom/)
- 🟢 [`remark-wiki-link`](https://github.com/landakram/remark-wiki-link) — new syntax for wiki links
  (rehype compatible)
- 🟢 [`remark-yaml-config`](https://github.com/remarkjs/remark-yaml-config) — configure remark w/
  YAML

<!--lint enable media-style-->

## List of utilities

For things that work with the syntax tree used in remark for markdown, see [_§ List of utilities_ in
`syntax-tree/mdast`][github-mdast-utilities]. For tools that work with **mdast** and other syntax
trees, see [_§ List of utilities_ in `syntax-tree/unist`][github-unist-utilities]. For tools that
work with the virtual file format used in remark, see [_§ List of utilities_ in
`vfile/vfile`][github-vfile-utilities].

## Use plugins

To use a plugin programmatically (from JavaScript), call the [`use()`][github-unified-use] method.
To use plugin with `remark-cli` (from the terminal), pass a [`--use` flag][github-unified-args-use]
or specify it in a [configuration file][github-unified-engine-config-files].

## Create plugins

To create a plugin, first read up on what they are in [_§ Plugin_ in
`unifiedjs/unified`][github-unified-plugin]. After that read [_§ Create a remark plugin_ on
`unifiedjs.com`][unifiedjs-create-a-plugin] for a practical introduction. Finally take one of the
existing plugins, which looks similar to what you’re about to make, and work from there. If you get
stuck, [discussions][health-discussions] is a good place to get help.

You should pick a name prefixed by `remark-` (such as `remark-lint`). **Do not use the `remark-`
prefix** if the thing you create doesn’t work with `remark().use()`: it isn’t a “plugin” and will
confuse users. If it works with mdast use `mdast-util-`. If it works with any unist tree use
`unist-util-`. If it works with virtual files use `vfile-`.

Use default exports to expose plugins from your packages. Add `remark-plugin` keywords in
`package.json`. Add a `remark-plugin` topic to your repo on GitHub. Create a pull request to add the
plugin here on this page!

[file-logo]: https://raw.githubusercontent.com/remarkjs/remark/1f338e72/logo.svg?sanitize=true
[github-mdast-utilities]: https://github.com/syntax-tree/mdast#list-of-utilities
[github-rehype-plugins]: https://github.com/rehypejs/rehype/blob/main/doc/plugins.md#list-of-plugins
[github-remark]: https://github.com/remarkjs/remark
[github-remark-awesome-remark]: https://github.com/remarkjs/awesome-remark
[github-remark-directive]: https://github.com/remarkjs/remark-directive
[github-topic-remark-plugin]: https://github.com/topics/remark-plugin
[github-unified-args-use]: https://github.com/unifiedjs/unified-args#--use-plugin
[github-unified-engine-config-files]: https://github.com/unifiedjs/unified-engine#config-files
[github-unified-plugin]: https://github.com/unifiedjs/unified#plugin
[github-unified-use]: https://github.com/unifiedjs/unified#processoruseplugin-options
[github-unist-utilities]: https://github.com/syntax-tree/unist#unist-utilities
[github-vfile-utilities]: https://github.com/vfile/vfile#list-of-utilities
[health-discussions]: https://github.com/remarkjs/remark/discussions
[unifiedjs-create-a-plugin]: https://unifiedjs.com/learn/guide/create-a-remark-plugin/

## Example remarkrc.yml

```yaml
output: true
plugins:
  frontmatter:
  github:
    repository: Fontlab/fl
    mentionStrong: false
  validate-links:
    repository: Fontlab/FontLabVI-help.wiki
  heading-gap:
    '1':
      after: "\n"
      before: "\n\n"
    '2':
      after: "\n"
      before: "\n"
  inline-links:
  slug:
  squeeze-paragraphs:
  yaml-config:
  autolink-headings:
  #behead:
  #  after:                               0
  #  depth:                               1
  #bracketed-spans:
  #defsplit:
  #kbd-plus:
  #mark:
  embed-images:
  external-links:
    target: '_blank'
  gemoji:
  html:
  #metadata:
  #  git:                                 true
  parse-yaml:
  #redact:
  #  beginMarker:                         ~~
  #  endMarker:                           ~~
  #  replacer:                            █
  #rehype:
  #  minify-whitespace:
  #relative-links:
  #  domainRegex:                         /http[s]*:\/\/[www.]*yoursite\.com[/]?/,
  #sectionize:
  toc:
  #unlink:
  #wiki-link-a:
  #  stringify:                            false
  #  mdPrefix:                             ""
  #  mdSuffix:                             ".md"
  #  mdSpace:                              "-"
  #  htmlClass:                            wikilink
  #  htmlPrefix:                           "../"
  #  htmlSuffix:                           "/"
  #  htmlSpace:                            "-"
  #unified:
  #  plugins:
  #    retext-english:
  #remark-retext:
  #remark-stringify:
  #stringify:
  #  emphasis:                            "_"
  #  strong:                              "*"
  lint:
  lint-alphabetize-lists: false
  #lint-appropriate-heading:              exact
  lint-blockquote-indentation: consistent
  lint-books-links: true
  lint-checkbox-character-style: { checked: x, unchecked: ' ' }
  lint-checkbox-content-indent: true
  lint-code-block-style: fenced
  lint-definition-case: true
  lint-definition-spacing: true
  lint-emphasis-marker: '_'
  lint-fenced-code-flag: { allowEmpty: true }
  lint-fenced-code-marker: '`'
  lint-file-extension: md
  lint-final-definition: true
  lint-final-newline: true
  lint-first-heading-level: 1
  lint-hard-break-spaces: true
  lint-heading-increment: true
  lint-heading-style: atx
  lint-link-title-style: consistent
  lint-list-item-bullet-indent: false
  lint-list-item-content-indent: true
  lint-list-item-indent: space
  lint-list-item-spacing: { checkBlanks: true }
  lint-maximum-heading-length: 300
  lint-maximum-line-length: 120
  lint-no-auto-link-without-protocol: false
  lint-no-blockquote-without-caret: false
  lint-no-blockquote-without-marker: false
  lint-no-consecutive-blank-lines: true
  lint-no-dead-urls: false
  lint-no-duplicate-definitions: true
  lint-no-duplicate-headings: true
  lint-no-emphasis-as-heading: true
  lint-no-empty-sections: true
  lint-no-file-name-articles: true
  lint-no-file-name-consecutive-dashes: true
  lint-no-file-name-irregular-characters: '\\.a-zA-Z0-9_\$\-'
  lint-no-file-name-mixed-case: true
  lint-no-file-name-outer-dashes: true
  lint-no-heading-content-indent: true
  lint-no-heading-indent: true
  lint-no-heading-punctuation: false
  lint-no-html: false
  lint-no-inline-padding: true
  lint-no-literal-urls: false
  lint-no-missing-blank-lines: true
  lint-no-multiple-toplevel-headings: true
  lint-no-shell-dollars: true
  lint-no-shortcut-reference-image: false
  lint-no-shortcut-reference-link: false
  lint-no-table-indentation: true
  lint-no-tabs: true
  lint-no-undefined-references: false
  lint-no-unused-definitions: true
  #lint-no-url-trailing-slash:            false
  lint-ordered-list-marker-style: .
  lint-ordered-list-marker-value: ordered
  lint-rule-style: '---'
  lint-strong-marker: '*'
  lint-table-cell-padding: padded
  lint-table-pipe-alignment: true
  lint-table-pipes: true
  lint-unordered-list-marker-style: '-'
  textr:
    options:
      locale: en-us
    plugins:
      - typographic-apostrophes
      - typographic-apostrophes-for-possessive-plurals
      #- typographic-arrows
      - typographic-colon
      - typographic-copyright
      - typographic-ellipses
      #- typographic-em-dashes
      - typographic-en-dashes
      - typographic-exclamation-mark
      - typographic-guillemets
      - typographic-math-symbols
      - typographic-percent
      - typographic-permille
      - typographic-question-mark
      - typographic-quotes
      - typographic-semicolon
      #- typographic-single-spaces
      - typographic-trademark
settings:
  bullet: '-'
  closeAtx: false
  commonmark: false
  emphasis: '_'
  entities: false
  fence: '`'
  fences: true
  footnotes: true
  gfm: true
  incrementListMarker: true
  listItemIndent: '1'
  looseTable: false
  paddedTable: true
  pedantic: false
  rule: '-'
  ruleRepetition: 3
  ruleSpaces: false
  setext: false
  spacedTable: true
  strong: '*'
  yaml: true
```

## Some other thing

```
const textrApostrophes = require('typographic-apostrophes')
const textrApostrophesForPlurals = require('typographic-apostrophes-for-possessive-plurals')
const textrCopyright = require('typographic-copyright')
const textrEllipses = require('typographic-ellipses')
const textrEmDashes = require('typographic-em-dashes')
const textrEnDashes = require('typographic-en-dashes')
const textrRegisteredTrademark = require('typographic-registered-trademark')
const textrSingleSpaces = require('typographic-single-spaces')
const textrTrademark = require('typographic-trademark')

const textrColon = require('typographic-colon/src')
const textrEmDash = require('typographic-em-dash/src')
const textrExclamationMark = require('typographic-exclamation-mark/src')
const textrGuillemets = require('typographic-guillemets/src')
const textrPercent = require('typographic-percent/src')
const textrPermille = require('typographic-permille/src')
const textrQuestionMark = require('typographic-question-mark/src')
const textrSemicolon = require('typographic-semicolon/src')

const gh = require('hast-util-sanitize/lib/github')
const katex = require('./sanitize-katex')
const merge = require('deepmerge')

const sanitizeConfig = merge.all([gh, katex, {
  tagNames: ['span', 'abbr', 'figure', 'figcaption', 'iframe'],
  attributes: {
    a: ['ariaHidden', 'class', 'className'],
    div: ['id', 'class', 'className'],
    span: ['id'],
    h1: ['ariaHidden'],
    h2: ['ariaHidden'],
    h3: ['ariaHidden'],
    abbr: ['title'],
    img: ['class'],
    code: ['className'],
    th: ['colspan', 'colSpan', 'rowSpan', 'rowspan'],
    td: ['colspan', 'colSpan', 'rowSpan', 'rowspan'],
    iframe: ['allowfullscreen', 'frameborder', 'height', 'src', 'width'],
  },
  protocols: {
    href: ['ftp', 'dav', 'sftp', 'magnet', 'tftp', 'view-source'],
    src: ['ftp', 'dav', 'sftp', 'tftp'],
  },
  clobberPrefix: '',
  clobber: [],
}])

const remarkConfig = {
  maxNesting: 100,
  reParse: {
    gfm: true,
    commonmark: false,
    footnotes: true,
    pedantic: false,
    /* sets list of known blocks to nothing, otherwise <h3>hey</h3> would become
    &#x3C;h3>hey&#x3C;/h3> instead of <p>&#x3C;h3>hey&#x3C;/h3></p> */
    blocks: [],
  },

  enableTextr: true,
  textr: {
    plugins: [
      textrApostrophes,
      textrApostrophesForPlurals,
      textrEllipses,
      textrEmDashes,
      textrEnDashes,
      textrCopyright,
      textrRegisteredTrademark,
      textrSingleSpaces,
      textrTrademark,

      textrColon,
      textrEmDash,
      textrExclamationMark,
      textrGuillemets,
      textrPercent,
      textrPermille,
      textrQuestionMark,
      textrSemicolon,
    ],
    options: {
      locale: 'fr',
    },
  },

  autolinkHeadings: {
    behaviour: 'append',
  },

  headingShifter: 0,

  remark2rehype: {
    allowDangerousHTML: true,
  },

  rehypeHighlight: {
    ignoreMissing: true,
    plainText: ['console'],
    aliases: {tex: ['latex']},
  },

  footnotesTitles: 'Retourner au texte de la note $id',

  alignBlocks: {
    center: 'align-center',
    right: 'align-right',
  },

  customBlocks: {
    secret: {
      classes: 'custom-block-spoiler',
      title: 'optional',
    },
    s: {
      classes: 'custom-block-spoiler',
      title: 'optional',
    },
    information: {
      classes: 'custom-block-information',
      title: 'optional',
    },
    i: {
      classes: 'custom-block-information',
      title: 'optional',
    },
    question: {
      classes: 'custom-block-question',
      title: 'optional',
    },
    q: {
      classes: 'custom-block-question',
      title: 'optional',
    },
    attention: {
      classes: 'custom-block-warning',
      title: 'optional',
    },
    a: {
      classes: 'custom-block-warning',
      title: 'optional',
    },
    erreur: {
      classes: 'custom-block-error',
      title: 'optional',
    },
    e: {
      classes: 'custom-block-error',
      title: 'optional',
    },
    neutre: {
      classes: 'custom-block-neutral',
      title: 'required',
    },
    n: {
      classes: 'custom-block-neutral',
      title: 'required',
    },
  },

  escapeEscaped: ['&'],

  emoticons: {
    emoticons: {
      ':ange:': '/static/smileys/ange.png',
      ':colere:': '/static/smileys/angry.gif',
      'o_O': '/static/smileys/blink.gif',
      ';)': '/static/smileys/clin.png',
      ':B': '/static/smileys/b.png',
      ':diable:': '/static/smileys/diable.png',
      ':D': '/static/smileys/heureux.png',
      '^^': '/static/smileys/hihi.png',
      ':o': '/static/smileys/huh.png',
      ':p': '/static/smileys/langue.png',
      ':magicien:': '/static/smileys/magicien.png',
      ':colere2:': '/static/smileys/mechant.png',
      ':ninja:': '/static/smileys/ninja.png',
      'x(': '/static/smileys/pinch.png',
      '>_<': '/static/smileys/pinch.png',
      'X/': '/static/smileys/pinch.png',
      ':pirate:': '/static/smileys/pirate.png',
      ":'(": '/static/smileys/pleure.png',
      ':lol:': '/static/smileys/rire.gif',
      ':honte:': '/static/smileys/rouge.png',
      ':-°': '/static/smileys/siffle.png',
      ':)': '/static/smileys/smile.png',
      ':soleil:': '/static/smileys/soleil.png',
      ':(': '/static/smileys/triste.png',
      ':euh:': '/static/smileys/unsure.gif',
      ':waw:': '/static/smileys/waw.png',
      ':zorro:': '/static/smileys/zorro.png',
      '^(;,;)^': '/static/smileys/cthulhu.png',
      ':popcorn:': '/static/smileys/popcorn.png',
    },
    classes: 'smiley',
  },

  math: {
    inlineMathDouble: true,
  },

  katex: {
    inlineMathDoubleDisplay: true,
  },

  iframes: {
    'www.dailymotion.com': {
      width: 480,
      height: 270,
      disabled: false,
      oembed: 'https://www.dailymotion.com/services/oembed',
    },
    'www.vimeo.com': {
      width: 500,
      height: 281,
      disabled: false,
      oembed: 'https://vimeo.com/api/oembed.json',
    },
    'vimeo.com': {
      width: 500,
      height: 281,
      disabled: false,
      oembed: 'https://vimeo.com/api/oembed.json',
    },
    'www.youtube.com': {
      width: 560,
      height: 315,
      disabled: false,
      oembed: 'https://www.youtube.com/oembed',
    },
    'youtube.com': {
      width: 560,
      height: 315,
      disabled: false,
      oembed: 'https://www.youtube.com/oembed',
    },
    'youtu.be': {
      width: 560,
      height: 315,
      disabled: false,
      oembed: 'https://www.youtube.com/oembed',
    },
    'soundcloud.com': {
      width: 500,
      height: 305,
      disabled: false,
      oembed: 'https://soundcloud.com/oembed',
    },
    'www.ina.fr': {
      tag: 'iframe',
      width: 620,
      height: 349,
      disabled: false,
      replace: [
        ['www.', 'player.'],
        ['/video/', '/player/embed/'],
      ],
      append: '/1/1b0bd203fbcd702f9bc9b10ac3d0fc21/560/315/1/148db8',
      removeFileName: true,
    },
    'www.jsfiddle.net': {
      tag: 'iframe',
      width: 560,
      height: 560,
      disabled: false,
      replace: [
        ['http://', 'https://'],
      ],
      append: 'embedded/result,js,html,css/',
      match: /https?:\/\/(www\.)?jsfiddle\.net\/([\w\d]+\/[\w\d]+\/\d+\/?|[\w\d]+\/\d+\/?|[\w\d]+\/?)$/,
      thumbnail: {
        format: 'http://www.unixstickers.com/image/data/stickers' +
        '/jsfiddle/JSfiddle-blue-w-type.sh.png',
      },
    },
    'jsfiddle.net': {
      tag: 'iframe',
      width: 560,
      height: 560,
      disabled: false,
      replace: [
        ['http://', 'https://'],
      ],
      append: 'embedded/result,js,html,css/',
      match: /https?:\/\/(www\.)?jsfiddle\.net\/([\w\d]+\/[\w\d]+\/\d+\/?|[\w\d]+\/\d+\/?|[\w\d]+\/?)$/,
      thumbnail: {
        format: 'http://www.unixstickers.com/image/data/stickers' +
        '/jsfiddle/JSfiddle-blue-w-type.sh.png',
      },
    },
  },

  captions: {
    external: {
      table: 'Table:',
      gridTable: 'Table:',
      code: 'Code:',
      math: 'Equation:',
      iframe: 'Video:',
    },
    internal: {
      math: 'Equation:',
      inlineMath: 'Equation:',
      image: 'Figure:',
    },
  },

  ping: {
    pingUsername: (_username) => true,
    userURL: (username) => `/membres/voir/${username}/`,
    usernameRegex: /\B@(?:\*\*([^*]+)\*\*|(\w+))/,
  },

  disableTokenizers: {},

  imagesDownload: {
    disabled: true,
    defaultImagePath: 'black.png',
    defaultOn: {
      statusCode: true,
      mimeType: false,
      fileTooBig: false,
    },
    downloadDestination: './img/',
    maxlength: 1000000,
    dirSizeLimit: 10000000,
  },
  sanitize: sanitizeConfig,
}

module.exports = remarkConfig

```

## Example

```
<script async type="module">import{unified}from"https://cdn.jsdelivr.net/npm/unified/+esm";import remarkParse from"https://cdn.jsdelivr.net/npm/remark-parse/+esm";import remarkFrontmatter from"https://cdn.jsdelivr.net/npm/remark-frontmatter/+esm";import remarkGfm from"https://cdn.jsdelivr.net/npm/remark-gfm/+esm";import remarkBreaks from"https://cdn.jsdelivr.net/npm/remark-breaks/+esm";import remarkRehype from"https://cdn.jsdelivr.net/npm/remark-rehype/+esm";import rehypeStringify from"https://cdn.jsdelivr.net/npm/rehype-stringify/+esm";import remarkFlexibleMarkers from"https://cdn.jsdelivr.net/npm/remark-flexible-markers/+esm";import remarkToc from"https://cdn.jsdelivr.net/npm/remark-toc/+esm";import remarkTypograf from"https://cdn.jsdelivr.net/npm/@mavrin/remark-typograf/+esm";import remarkGithubAdmonitionsToDirectives from"https://cdn.jsdelivr.net/npm/remark-github-admonitions-to-directives/+esm";import remarkDirective from"https://cdn.jsdelivr.net/npm/remark-directive/+esm";import remarkDirectiveRehype from"https://cdn.jsdelivr.net/npm/remark-directive-rehype/+esm";import{remarkExtendedTable,extendedTableHandlers}from"https://cdn.jsdelivr.net/npm/remark-extended-table/+esm";import remarkImages from"https://cdn.jsdelivr.net/npm/remark-images/+esm";import remarkSectionize from"https://cdn.jsdelivr.net/npm/remark-sectionize/+esm";import remarkTextr from"https://cdn.jsdelivr.net/npm/remark-textr/+esm";import remarkYamlConfig from"https://cdn.jsdelivr.net/npm/remark-yaml-config/+esm";import{remarkDefinitionList,defListHastHandlers}from"https://cdn.jsdelivr.net/npm/remark-definition-list/+esm";import remarkEmbed from"https://cdn.jsdelivr.net/npm/@flowershow/remark-embed/+esm";import remarkFigureCaption from"https://cdn.jsdelivr.net/npm/@microflash/remark-figure-caption/+esm";const textrPlugins=["typographic-apostrophes","typographic-apostrophes-for-possessive-plurals","typographic-arrows","typographic-colon","typographic-copyright","typographic-ellipses","typographic-en-dashes","typographic-exclamation-mark","typographic-guillemets","typographic-math-symbols","typographic-numbers","typographic-percent","typographic-permille","typographic-question-mark","typographic-quotes","typographic-registered-trademark","typographic-semicolon","typographic-single-spaces","typographic-trademark"].map((e=>`https://cdn.jsdelivr.net/npm/${e}/+esm`)),body=document.body,head=document.head;body.classList.add("markdown-body"),body.style.cssText="max-width: 800px; margin: auto;",unified().use(remarkParse).use(remarkGfm).use(remarkFrontmatter).use(remarkYamlConfig).use(remarkTextr,{options:{locale:"en-us"},plugins:textrPlugins}).use(remarkEmbed).use(remarkGithubAdmonitionsToDirectives).use(remarkDirective).use(remarkDirectiveRehype).use(remarkFlexibleMarkers).use(remarkTypograf,{locale:["en-US"],keywords:[":)"]}).use(remarkToc,{tight:!0}).use(remarkSectionize).use(remarkExtendedTable).use(remarkDefinitionList).use(remarkFigureCaption).use(remarkImages).use(remarkBreaks).use(remarkRehype,null,{handlers:{...extendedTableHandlers}}).use(rehypeStringify).process(body.innerHTML.replace(/&gt;/g,">").replace(/&lt;/g,"<").replace(/\+\+/g,"`")).then((e=>body.innerHTML=e)).catch((e=>{throw e})),head.innerHTML+='<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/github-markdown-css/github-markdown.css">';</script>
```

## Example 2

```
<script type="module">
import { init, parse as wasmParse, ParseFlags } from 'https://cdn.jsdelivr.net/npm/markdown-wasm-es@1/+esm';

// Constants for styling and configuration
const CONFIG = {
    styles: {
        base: [
            'https://cdn.jsdelivr.net/npm/github-markdown-css/github-markdown-light.min.css',
            'https://cdn.jsdelivr.net/npm/highlight.js@11/styles/stackoverflow-light.min.css',
            'https://cdn.jsdelivr.net/npm/uikit@3/dist/css/uikit.min.css',
            'https://cdn.jsdelivr.net/npm/@fancyapps/ui@5/dist/fancybox/fancybox.css'
        ],
        inlineCSS: `
            html { font-size: 18px !important; }
            body {
                max-width: 800px;
                margin: 0 auto;
                padding: 2rem;
            }
        `,
    },
    scripts: [
        'https://cdn.jsdelivr.net/npm/@fancyapps/ui@5/dist/fancybox/fancybox.umd.js',
        'https://cdn.jsdelivr.net/npm/uikit@3/dist/js/uikit.min.js',
        'https://cdn.jsdelivr.net/npm/uikit@3/dist/js/uikit-icons.min.js'
    ],
    wasmUrl: 'https://esm.sh/markdown-wasm@1/dist/markdown.wasm'
};

// List of typographic plugins to load
const TYPOGRAPHIC_PLUGINS = [
    'typographic-apostrophes',
    'typographic-apostrophes-for-possessive-plurals',
    'typographic-arrows',
    'typographic-colon',
    'typographic-copyright',
    'typographic-ellipses',
    'typographic-en-dashes',
    'typographic-exclamation-mark',
    'typographic-guillemets',
    'typographic-math-symbols',
    'typographic-numbers',
    'typographic-percent',
    'typographic-permille',
    'typographic-question-mark',
    'typographic-quotes',
    'typographic-registered-trademark',
    'typographic-semicolon',
    'typographic-single-spaces',
    'typographic-trademark'
];

async function initializeStyles() {
    const head = document.head;
    const body = document.body;

    // Setup markdown body styling
    body.classList.add('markdown-body', 'uk-container', 'uk-container-small');
    body.style.cssText = 'visibility: hidden;';

    // Add all stylesheets
    const stylePromises = CONFIG.styles.base.map(href => {
        const link = document.createElement('link');
        link.rel = 'stylesheet';
        link.href = href;
        link.type = 'text/css';
        head.appendChild(link);
        return new Promise((resolve, reject) => {
            link.onload = resolve;
            link.onerror = reject;
        });
    });

    // Add inline styles
    const style = document.createElement('style');
    style.textContent = CONFIG.styles.inlineCSS;
    head.appendChild(style);

    await Promise.all(stylePromises);
}

async function loadScripts() {
    const head = document.head;
    const scriptPromises = CONFIG.scripts.map(src => {
        const script = document.createElement('script');
        script.src = src;
        script.async = true;
        head.appendChild(script);
        return new Promise((resolve, reject) => {
            script.onload = resolve;
            script.onerror = reject;
        });
    });

    await Promise.all(scriptPromises);
}

function preprocessMarkdown(content) {
    return content
        .replace(/&[lg]t;/g, match => match[1] === 'l' ? '<' : '>')
        .replace(/==|\+\+/g, match => match === '==' ? '**' : '`')
        .replace(/\[\[([^\]]+)\]\]/g, '[$1]($1)') // Wiki-style links
        .replace(/~~([^~]+)~~/g, '<del>$1</del>'); // Strikethrough
}

async function loadPlugins() {
    const [
        { unified },
        remarkParse,
        remarkFrontmatter,
        remarkGfm,
        remarkRehype,
        rehypeHighlight,
        rehypeStringify,
        remarkToc,
        remarkTypograf,
        remarkDirective,
        { remarkExtendedTable, extendedTableHandlers },
        remarkImages,
        remarkSectionize,
        remarkTextr,
        remarkYamlConfig,
        { remarkDefinitionList },
        remarkEmbed,
        remarkFigureCaption,
        remarkIns,
        rehypeDocument,
        rehypeMeta,
        remarkFlexibleMarkers,
        rehypeParse,
        remarkMermaid,
        remarkEmoji,
        remarkFootnotes
    ] = await Promise.all([
        import('https://esm.sh/unified@11?bundle'),
        import('https://esm.sh/remark-parse@11?bundle'),
        import('https://esm.sh/remark-frontmatter@5?bundle'),
        import('https://esm.sh/remark-gfm@4?bundle'),
        import('https://esm.sh/remark-rehype@11?bundle'),
        import('https://esm.sh/rehype-highlight@6?bundle'),
        import('https://esm.sh/rehype-stringify?bundle'),
        import('https://esm.sh/remark-toc?bundle'),
        import('https://esm.sh/@mavrin/remark-typograf?bundle'),
        import('https://esm.sh/remark-directive?bundle'),
        import('https://esm.sh/remark-extended-table?bundle'),
        import('https://esm.sh/remark-images?bundle'),
        import('https://esm.sh/remark-sectionize?bundle'),
        import('https://esm.sh/remark-textr?bundle'),
        import('https://esm.sh/remark-yaml-config?bundle'),
        import('https://esm.sh/remark-definition-list?bundle'),
        import('https://esm.sh/@flowershow/remark-embed?bundle'),
        import('https://esm.sh/@microflash/remark-figure-caption?bundle'),
        import('https://esm.sh/remark-ins@1?bundle'),
        import('https://esm.sh/rehype-document@6?bundle'),
        import('https://esm.sh/rehype-meta@3?bundle'),
        import('https://esm.sh/remark-flexible-markers@1?bundle'),
        import('https://esm.sh/rehype-parse@8?bundle'),
        import('https://esm.sh/remark-mermaid@0.2?bundle'),
        import('https://esm.sh/remark-emoji@4?bundle'),
        import('https://esm.sh/remark-footnotes@4?bundle')
    ]);

    // Load typographic plugins
    const typographicPlugins = await Promise.all(
        TYPOGRAPHIC_PLUGINS.map(plugin =>
            import(`https://esm.sh/${plugin}?bundle`).then(module => module.default)
        )
    );

    return {
        unified,
        plugins: {
            remarkParse,
            remarkFrontmatter,
            remarkGfm,
            remarkRehype,
            rehypeHighlight,
            rehypeStringify,
            remarkToc,
            remarkTypograf,
            remarkDirective,
            remarkExtendedTable,
            extendedTableHandlers,
            remarkImages,
            remarkSectionize,
            remarkTextr,
            remarkYamlConfig,
            remarkDefinitionList,
            remarkEmbed,
            remarkFigureCaption,
            remarkIns,
            rehypeDocument,
            rehypeMeta,
            remarkFlexibleMarkers,
            rehypeParse,
            remarkMermaid,
            remarkEmoji,
            remarkFootnotes
        },
        typographicPlugins
    };
}

async function processMarkdown(content, { unified, plugins, typographicPlugins }) {
    const processor = unified()
        .use(plugins.remarkParse.default)
        .use(plugins.remarkFrontmatter.default)
        .use(plugins.remarkYamlConfig.default)
        .use(plugins.remarkTextr.default, {
            options: { locale: 'en-us' },
            plugins: typographicPlugins
        })
        .use(plugins.remarkEmbed.default)
        .use(plugins.remarkDirective.default)
        .use(plugins.remarkTypograf.default, {
            locale: ['en-US'],
            keywords: [':)']
        })
        .use(plugins.remarkToc.default, { tight: true })
        .use(plugins.remarkGfm.default)
        .use(plugins.remarkSectionize.default)
        .use(plugins.remarkExtendedTable)
        .use(plugins.remarkDefinitionList)
        .use(plugins.remarkFigureCaption.default)
        .use(plugins.remarkImages.default)
        .use(plugins.remarkIns.default)
        .use(plugins.remarkFlexibleMarkers.default)
        .use(plugins.remarkMermaid.default)
        .use(plugins.remarkEmoji.default)
        .use(plugins.remarkFootnotes.default)
        .use(plugins.remarkRehype.default, null, {
            handlers: { ...plugins.extendedTableHandlers }
        })
        .use(plugins.rehypeHighlight.default, {
            ignoreMissing: true,
            detect: true,
            subset: false
        })
        .use(plugins.rehypeDocument.default, {
            title: 'Document',
            css: CONFIG.styles.base,
            js: CONFIG.scripts,
            style: CONFIG.styles.inlineCSS,
            doctype: '<!DOCTYPE html>',
            language: 'en',
            meta: [{ charset: 'utf-8' }, { viewport: 'width=device-width, initial-scale=1' }]
        })
        .use(plugins.rehypeMeta.default, {
            og: true,
            twitter: true,
            copyright: true,
            type: 'article'
        })
        .use(plugins.rehypeStringify.default);

    const result = await processor.process(content);
    return result.toString();
}

async function main() {
    try {
        // Initialize page styles and scripts
        await Promise.all([
            initializeStyles(),
            loadScripts()
        ]);

        // Get and preprocess content
        const content = preprocessMarkdown(document.body.innerHTML);

        // Initialize markdown-wasm
        await init(CONFIG.wasmUrl);

        // First pass with markdown-wasm
        const initialHtml = wasmParse(content, {
            parseFlags: ParseFlags.DEFAULT | ParseFlags.SMART | ParseFlags.TABLES | ParseFlags.STRIKETHROUGH,
            format: 'html',
            allowJSURIs: false
        });
        document.body.innerHTML = initialHtml;

        // Load and initialize plugins
        const pluginData = await loadPlugins();

        // Process with unified and plugins
        const finalHtml = await processMarkdown(content, pluginData);

        // Update page with final result
        document.documentElement.innerHTML = finalHtml;

        // Final cleanup and styling
        const body = document.body;
        body.innerHTML = body.innerHTML
            .replace(/&gt;/g, '>')
            .replace(/&lt;/g, '<')
            .replace(/==/g, '**')
            .replace(/\+\+/g, '`');

        body.classList.add('markdown-body', 'uk-container', 'uk-container-small');
        body.style.cssText = 'visibility: visible;';

        // Initialize Fancybox
        Fancybox.bind("[data-fancybox]", {
            // Your custom options
        });

    } catch (error) {
        console.error('Error processing markdown:', error);
        document.body.innerHTML = `<div class="error">Error processing markdown: ${error.message}</div>`;
        document.body.style.visibility = 'visible';
    }
}

// Start processing
main().catch(console.error);
</script>
```

## VSCode Extension unifiedjs.vscode-remark

- https://marketplace.visualstudio.com/items?itemName=unifiedjs.vscode-remark
- https://github.com/remarkjs/vscode-remark

Token Usage: GitHub Tokens: 4048 LLM Input Tokens: 0 LLM Output Tokens: 0 Total Tokens: 4048

FileTree: .github/workflows/bb.yml .github/workflows/main.yml .github/workflows/publish.yml
.gitignore .vscode/launch.json .vscode/tasks.json changelog.md package.json package.schema.json
readme.md src/extension.js test/index.test.js tsconfig.json

Analysis: .github/workflows/bb.yml

```.yml
name: bb
on:
  issues:
    types: [opened, reopened, edited, closed, labeled, unlabeled]
  pull_request_target:
    types: [opened, reopened, edited, closed, labeled, unlabeled]
jobs:
  main:
    runs-on: ubuntu-latest
    steps:
      - uses: unifiedjs/beep-boop-beta@main
        with:
          repo-token: ${{secrets.GITHUB_TOKEN}}

```

.github/workflows/main.yml

```.yml
name: main

on: [push, pull_request]

jobs:
  build:
    strategy:
      matrix:
        os: [macos-latest, ubuntu-latest, windows-latest]
    runs-on: ${{matrix.os}}
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install
      - run: npm test
        if: ${{matrix.os!='ubuntu-latest'}}
      - run: xvfb-run npm test
        if: ${{matrix.os=='ubuntu-latest'}}

  package:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install
      - run: npx vsce package
      - uses: actions/upload-artifact@v4
        with:
          name: vscode-remark.vsix
          path: '*.vsix'

```

.github/workflows/publish.yml

```.yml
name: publish

on:
  release:
    types: [published]

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install
      - run: npx vsce package
      - run: npx vsce publish --packagePath *.vsix
        env:
          VSCE_PAT: ${{secrets.VSCE_TOKEN}}
      - run: npx ovsx publish --packagePath *.vsix
        env:
          OVSX_PAT: ${{secrets.OPEN_VSX_TOKEN}}

```

.gitignore

```.gitignore
logs/
node_modules/
out/
*.log
*.vsix
.DS_Store
.vscode*
yarn.lock

```

.vscode/launch.json

```.json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Launch Extension",
      "type": "extensionHost",
      "request": "launch",
      "runtimeExecutable": "${execPath}",
      "autoAttachChildProcesses": true,
      "args": [
        "--disable-updates",
        "--disable-workspace-trust",
        "--profile-temp",
        "--skip-release-notes",
        "--skip-welcome",
        "${workspaceFolder}/readme.md",
        "--extensionDevelopmentPath=${workspaceFolder}"
      ],
      "skipFiles": ["<node_internals>/**", "**/node_modules/vscode-*/**"],
      "preLaunchTask": "build"
    }
  ]
}

```

.vscode/tasks.json

```.json
{
  "version": "2.0.0",
  "tasks": [
    {
      "type": "shell",
      "command": "npm",
      "args": ["run", "build", "--", "--sourcemap"],
      "label": "build",
      "group": {
        "kind": "build",
        "isDefault": true
      }
    }
  ]
}

```

changelog.md

# Changelog

See [GitHub Releases][releases] for the changelog.

[releases]: https://github.com/remarkjs/vscode-remark/releases

package.json

```.json
{
  "name": "vscode-remark",
  "version": "3.0.0",
  "description": "Lint and format markdown code with remark",
  "license": "MIT",
  "private": true,
  "keywords": [
    "markdown",
    "remark",
    "format",
    "lint",
    "validate"
  ],
  "repository": {
    "type": "git",
    "url": "https://github.com/remarkjs/vscode-remark"
  },
  "bugs": "https://github.com/remarkjs/vscode-remark/issues",
  "funding": {
    "type": "opencollective",
    "url": "https://opencollective.com/unified"
  },
  "author": "Denis Malinochkin <dmalinochkin@rambler.ru>",
  "contributors": [
    "Denis Malinochkin <dmalinochkin@rambler.ru>",
    "Titus Wormer <tituswormer@gmail.com> (https://wooorm.com)",
    "Remco Haszing <remcohaszing@gmail.com>",
    "Asbjørn Ulsberg <asbjorn@ulsberg.no>",
    "Christian Murphy <christian.murphy.42@gmail.com>"
  ],
  "main": "out/extension.js",
  "engines": {
    "vscode": "^1.67.0"
  },
  "devDependencies": {
    "@types/node": "^20.0.0",
    "@types/vscode": "^1.0.0",
    "@vscode/test-electron": "^2.0.0",
    "@vscode/vsce": "^2.0.0",
    "esbuild": "^0.20.0",
    "ovsx": "^0.9.0",
    "prettier": "^3.0.0",
    "remark-cli": "^12.0.0",
    "remark-language-server": "^3.0.0",
    "remark-preset-wooorm": "^10.0.0",
    "typescript": "^5.0.0",
    "vscode-languageclient": "^9.0.0",
    "xo": "^0.58.0"
  },
  "scripts": {
    "vscode:prepublish": "npm run build",
    "build": "esbuild extension=src/extension.js remark-language-server --bundle --platform=node --target=node16 --format=cjs --external:vscode --outdir=out --minify",
    "format": "remark . -qfo && prettier . -w --log-level warn && xo --fix",
    "test-api": "node --conditions development test.mjs",
    "test": "npm run build && npm run format && npm run test-api"
  },
  "prettier": {
    "tabWidth": 2,
    "useTabs": false,
    "singleQuote": true,
    "bracketSpacing": false,
    "semi": false,
    "trailingComma": "none"
  },
  "xo": {
    "prettier": true,
    "rules": {
      "unicorn/prefer-module": "off"
    }
  },
  "remarkConfig": {
    "plugins": [
      "preset-wooorm",
      [
        "remark-lint-no-html",
        false
      ]
    ]
  },
  "displayName": "remark",
  "publisher": "unifiedjs",
  "icon": "icon.png",
  "categories": [
    "Formatters",
    "Linters"
  ],
  "activationEvents": [
    "onLanguage:markdown"
  ],
  "qna": "https://github.com/orgs/remarkjs/discussions",
  "sponsor": {
    "url": "https://github.com/sponsors/unifiedjs"
  },
  "capabilities": {
    "virtualWorkspaces": {
      "supported": false,
      "description": "This extension relies on the file system to load remark and plugins."
    },
    "untrustedWorkspaces": {
      "supported": false,
      "description": "This extension loads configuration files and plugins from workspace and executes them."
    }
  },
  "contributes": {
    "configuration": {
      "title": "remark",
      "properties": {
        "remark.requireConfig": {
          "type": "boolean",
          "default": false,
          "markdownDescription": "If true, only perform actions if a [configuration file](https://github.com/remarkjs/vscode-remark#configuration-file) is found."
        }
      }
    },
    "jsonValidation": [
      {
        "fileMatch": [
          ".remarkrc",
          ".remarkrc.json"
        ],
        "url": "https://json.schemastore.org/remarkrc"
      },
      {
        "fileMatch": "package.json",
        "url": "./package.schema.json"
      }
    ],
    "languages": [
      {
        "id": "ignore",
        "filenames": [
          ".remarkignore"
        ]
      },
      {
        "id": "json",
        "filenames": [
          ".remarkrc"
        ]
      }
    ]
  }
}

```

package.schema.json

```.json
{
  "properties": {
    "remarkConfig": {
      "description": "remark configuration",
      "$ref": "https://json.schemastore.org/remarkrc"
    }
  }
}

```

readme.md

# remark for Visual Studio Code

[![Build][build-badge]][build] [![Downloads][downloads-badge]][marketplace]
[![Sponsors][sponsors-badge]][collective] [![Backers][backers-badge]][collective]
[![Chat][chat-badge]][chat]

Visual Studio Code extension to format and lint markdown files with remark.

## Contents

- [What is this?](#what-is-this)
- [When should I use this?](#when-should-i-use-this)
- [Install](#install)
- [Use](#use)
- [Configuration file](#configuration-file)
- [Settings](#settings)
- [Formatting](#formatting)
- [Plugins](#plugins)
- [Compatibility](#compatibility)
- [Security](#security)
- [Contribute](#contribute)
- [License](#license)

## What is this?

This project is a Visual Studio Code (VS Code) extension that you can use in your editor to inspect
and change markdown files. This extension is built around remark, which is a very popular ecosystem
of plugins that work with markdown. You can choose from the 150+ plugins that already exist or make
your own.

See [remark][] for info on what the remark ecosystem is.

## When should I use this?

You can use this extension if you want to check (lint) and format markdown files from within your
editor.

To configure this extension, you define your preferred markdown style in a configuration file
(`.remarkrc`, `.remarkrc.js`, etc. or in `package.json`). This file is picked up by `vscode-remark`
and other tools (useful for contributors that don’t use VS Code).

The configuration file is also used by [`remark-cli`][remark-cli], which is recommended to be used
alongside `vscode-remark`, as an npm script and/or in CI, to enforce the markdown style.

## Install

[Get it on the VS Code Marketplace][marketplace] or install it by using Quick Open
(<kbd>Ctrl</kbd> + <kbd>P</kbd>) and running the following:

```txt
ext install unifiedjs.vscode-remark
```

## Use

To use this extension, set up [`remark-cli`][remark-cli] like you normally would in your project
with a configuration file. The extension will find the configuration in your workspace just like
running `remark-cli` in your terminal would. You will be able to see your linter work as you type
and you can format your code if you want it to.

Now, you can open markdown files in your project, and you’ll see squiggly lines and warnings in the
`Problems` pane if the code doesn’t adhere to the coding standards. Here’s an example that should
produce problems you can use to verify:

```markdown
1. Hello, _Jupiter_ and _Neptune_!
```

## Configuration file

`remark-language-server` uses the same configuration files as [`remark-cli`][remark-cli]. These
files are:

- `.remarkrc`
- `.remarkrc.cjs`
- `.remarkrc.js`
- `.remarkrc.json`
- `.remarkrc.mjs`
- `.remarkrc.yaml`
- `.remarkrc.yml`
- `package.json`

Language clients should notify the language server if these files change. They are looked up
starting at the folder where the checked markdown file exists.

## Settings

This extension supports the following settings:

- `remark.requireConfig` (`boolean`, default: `false`) — If true, only perform actions if a
  [configuration file][configuration-file] is found.

## Formatting

This extension can format markdown files.

To format a file, pull up the command pallete (<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>),
choose `Format Document With…`, and select `remark`.

To make `vscode-remark` the default formatter for markdown, add the following to your
`settings.json` (which you can open with <kbd>Ctrl</kbd> + <kbd>,</kbd>):

```json
{
  "[markdown]": {
    "editor.defaultFormatter": "unifiedjs.vscode-remark"
  }
}
```

Now markdown documents can be formatted using <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>I</kbd>.

You can optionally choose to automatically format when saving with `editor.formatOnSave`:

```json
{
  "[markdown]": {
    "editor.defaultFormatter": "unifiedjs.vscode-remark",
    "editor.formatOnSave": true
  }
}
```

## Plugins

The **remark** ecosystem has a variety of plugins available. Most notably you’ll want to check out
[`remark-lint`][remark-lint]. See this curated [list of plugins][list-of-plugins] for more remark
plugins.

## Compatibility

This extension is compatible with Visual Studio Code versions 1.67.0 and greater.

## Security

This plugin loads configuration files, plugins, and presets from your workspace. Only use this
plugin in workspaces you trust.

## Contribute

See [`contributing.md`][contributing] in [`remarkjs/.github`][health] for ways to get started. See
[`support.md`][support] for ways to get help. Join us in [Discussions][chat] to chat with the
community and contributors.

This project has a [code of conduct][coc]. By interacting with this repository, organization, or
community you agree to abide by its terms.

## License

[MIT][license] © Denis Malinochkin

<!-- Definitions -->

[build-badge]: https://github.com/remarkjs/vscode-remark/workflows/main/badge.svg
[build]: https://github.com/remarkjs/vscode-remark/actions
[configuration-file]: #configuration-file
[downloads-badge]: https://img.shields.io/visual-studio-marketplace/d/unifiedjs.vscode-remark
[chat-badge]: https://img.shields.io/badge/chat-discussions-success.svg
[chat]: https://github.com/remarkjs/remark/discussions
[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg
[backers-badge]: https://opencollective.com/unified/backers/badge.svg
[health]: https://github.com/remarkjs/.github
[contributing]: https://github.com/remarkjs/.github/blob/main/contributing.md
[support]: https://github.com/remarkjs/.github/blob/main/support.md
[coc]: https://github.com/remarkjs/.github/blob/main/code-of-conduct.md
[collective]: https://opencollective.com/unified
[license]: license
[marketplace]: https://marketplace.visualstudio.com/items?itemName=unifiedjs.vscode-remark
[remark-lint]: https://github.com/remarkjs/remark-lint
[remark]: https://github.com/remarkjs/remark
[remark-cli]: https://github.com/remarkjs/remark/tree/main/packages/remark-cli
[list-of-plugins]: https://github.com/remarkjs/remark/blob/main/doc/plugins.md

src/extension.js

```.js
import {workspace} from 'vscode'
import {LanguageClient, TransportKind} from 'vscode-languageclient/node.js'

/**
 * @type {LanguageClient}
 */
let client

/**
 * @param {import('vscode').ExtensionContext} context
 */
export async function activate(context) {
  client = new LanguageClient(
    'remark',
    {
      module: context.asAbsolutePath('out/remark-language-server.js'),
      transport: TransportKind.ipc
    },
    {
      documentSelector: [{scheme: 'file', language: 'markdown'}],
      synchronize: {
        fileEvents: [
          workspace.createFileSystemWatcher(
            '**/.remark{ignore,rc,rc.cjs,rc.js,rc.json,rc.mjs,rc.yaml,rc.yml}'
          ),
          workspace.createFileSystemWatcher('**/package.json')
        ]
      }
    }
  )

  await client.start()
}

export async function deactivate() {
  if (client) {
    await client.stop()
  }
}

```

test/index.test.js

```.js
const assert = require('node:assert/strict')
const fs = require('node:fs/promises')
const path = require('node:path')
const {test} = require('node:test')
const {commands, extensions, window, workspace} = require('vscode')

module.exports.run = async () => {
  const filePath = path.join(__dirname, 'test.md')

  const extension = extensions.getExtension('unifiedjs.vscode-remark')
  await extension?.activate()

  await test('use the language server', async () => {
    await fs.writeFile(filePath, '- remark\n- lsp\n- vscode\n')
    const document = await workspace.openTextDocument(filePath)
    await window.showTextDocument(document)
    await commands.executeCommand('editor.action.formatDocument')

    assert.equal(document.getText(), '*   remark\n*   lsp\n*   vscode\n')
  })

  await fs.rm(filePath, {force: true})
}

```

tsconfig.json

```.json
{
  "exclude": ["out"],
  "compilerOptions": {
    "checkJs": true,
    "module": "node16",
    "target": "es2021",
    "lib": ["es2021"],
    "noEmit": true,
    "strict": true
  }
}

```
