# Lasik for Claude Code

A dark, high contrast theme for [Claude Code](https://code.claude.com), made for sensitive eyes and long reading sessions. It's part of the Lasik family (also for [VS Code](https://github.com/LasikTheme/vscode), [Konsole](https://github.com/LasikTheme/konsole) and [Kitty](https://github.com/LasikTheme/kitty)), and every color comes from the [Lasik palette](https://github.com/LasikTheme/palette).

- **Easy to tell who said what:** your messages sit on their own periwinkle-slate background.
- **High contrast:** all text is at least 7:1 (WCAG AAA) against the background.
- **No halo:** the main text is a light lavender (`#e8ecfd`) instead of pure white, which glows on a dark background.
- **Color-blind friendly base:** colors the theme doesn't set come from Claude Code's `dark-daltonized` theme.

## Install

Claude Code loads custom themes from `~/.claude/themes/`.

```sh
mkdir -p ~/.claude/themes
ln -s "$PWD/lasik.json" ~/.claude/themes/lasik.json
```

- `mkdir -p`: creates the folder if it doesn't exist (`-p` means "no error if it's already there").
- `ln -s`: makes a link instead of a copy, so updates to this repo apply right away. Run it from this folder.

Then restart Claude Code once, run `/theme` and pick **Lasik**. Claude Code watches the themes folder and reloads a theme when its file changes.

## What you can customize

A Claude Code theme is a JSON file with three fields: `name`, `base` (the built-in theme that fills in everything you don't set) and `overrides` (token → color). Colors can be `#rrggbb`, `#rgb`, `rgb(r,g,b)`, `ansi256(n)` or `ansi:<name>`. The full token list is in the [Claude Code docs](https://code.claude.com/docs/en/terminal-config.md#create-a-custom-theme).

| You can set | Tokens |
|---|---|
| Text and accent | `text`, `claude` (accent, spinner, assistant label), `inactive` (hints, timestamps), `subtle` (faint borders), `suggestion`, `permission`, `remember`, `inverseText` |
| Status colors | `success`, `error`, `warning`, `merged` |
| Input box and modes | `promptBorder`, `planMode`, `autoAccept`, `bashBorder`, `ide`, `fastMode` |
| Message backgrounds | `userMessageBackground` (and its hover), `bashMessageBackgroundColor` (`!` commands), `memoryBackgroundColor`, `selectionBg` |
| Diffs | `diffAdded`, `diffRemoved` (whole lines), `diffAddedWord`, `diffRemovedWord` (changed words), and dimmed versions |
| Spinner shimmer | `claudeShimmer`, `warningShimmer`, `inactiveShimmer`, … |
| Labels and meters | `briefLabelYou`, `briefLabelClaude`, `rate_limit_fill`, `rate_limit_empty` |
| Subagent and rainbow colors | `red_FOR_SUBAGENTS_ONLY` … and `rainbow_*` |

Other settings, outside the theme file:

- **Syntax highlighting on or off:** Ctrl+T in `/theme`, or `syntaxHighlightingDisabled` in `~/.claude/settings.json`.
- **Status line** (the bar under the input box): any command's output, set with `/statusline`.
- **Session color:** `/color`.
- **Keyboard shortcuts:** `/keybindings`.

## What you can't customize

- **Colors of code** in code blocks and diffs: they come from the `base` theme.
- **Inline code** color (reported by users, not confirmed in the docs).
- **The terminal itself:** its background, font and the 16 terminal colors belong to your terminal (for Kitty, use the [Lasik Kitty theme](https://github.com/LasikTheme/kitty)).
- **Tool calls:** there is no token for the tool name (`Bash`, `Read`, …), its arguments or its output. They use the general `text` and `inactive` colors. The ⏺ dot in front of a tool call appears to follow `success`, `error` and `inactive` (not confirmed in the docs), so changing those changes every success, error and hint message too.
- **Command and tool output:** there is no token for the text of command output. It uses the general text and hint colors as far as the docs show. Only the `!` commands you type yourself have their own colors: `bashBorder` and `bashMessageBackgroundColor`.
- **Fonts, sizes, spacing and layout.**

Unknown tokens and invalid colors are ignored, so a typo doesn't break the theme, it just has no effect.
