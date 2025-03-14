# tmux-compose-sh

Simple tmux compose bash script (inspired by docker compose)

## Dependencies

Arch Linux:
```
$ pacman -S yq
```

## Example

```yaml
version: '1'

sessions:
  - name: dev
    windows:
      - name: editor
        command: vim
      - name: terminal
        command: echo "Welcome to terminal window"
      - name: server
        command: echo "Server window ready"
        panes:
          - command: echo "Main server pane"
          - command: echo "Logs pane"
            split: vertical
          - command: echo "Testing pane"
            split: horizontal
        layout: main-vertical
      - name: database
        panes:
          - command: echo "Database client"
          - command: echo "Database logs"
            split: horizontal

  - name: monitoring
    windows:
      - name: system
        command: htop
      - name: network
        command: echo "Network monitoring"
```

```bash
./tmux-compose.sh up
```
