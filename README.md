[Workflow example screenshot](images/screenshot.png)

# setup

## install neovim

- [installation guide](https://github.com/neovim/neovim/blob/master/INSTALL.md)

## install tmux

- [installation guide](https://github.com/tmux/tmux/wiki/Installing)

## install tmuxifier

- [installation guide](https://github.com/jimeh/tmuxifier)

## install opencode

```bash
npm install -g opencode-ai
```

# Tmuxifier session example

```bash
tmuxifier new-session 'example'
```

```bash
window_root "~/github/example/"

if initialize_session "example"; then
  new_window "example"

  split_v 20
  run_cmd "cd server && make run-api"
  split_h 50
  run_cmd "cd client && npm run dev"

  select_pane 0 
  run_cmd "cd client && nvim ."
  split_h 2
  run_cmd "cd client && opencode"
  select_pane 0
fi

finalize_and_go_to_session
```

```bash
tmuxifier load-session example
```
