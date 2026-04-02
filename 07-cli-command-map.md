# CLI Command Map

## Giris Noktasi

CLI giris noktasi `src/main.py` dosyasidir. Parser `build_parser()` icinde kurulur, komutlar `main()` icinde `if args.command == ...` bloklariyla handle edilir.

Kaynaklar:
- [src/main.py#L21](/home/eren/Desktop/claw-code/src/main.py#L21)
- [src/main.py#L98](/home/eren/Desktop/claw-code/src/main.py#L98)

## Komutlar ve Baglandiklari Yerler

### Ozet ve Envanter Komutlari

- `summary`: `QueryEnginePort.from_workspace().render_summary()`
- `manifest`: `build_port_manifest().to_markdown()`
- `parity-audit`: `run_parity_audit().to_markdown()`
- `setup-report`: `run_setup().as_markdown()`
- `command-graph`: `build_command_graph().as_markdown()`
- `tool-pool`: `assemble_tool_pool().as_markdown()`
- `bootstrap-graph`: `build_bootstrap_graph().as_markdown()`
- `subsystems`: `build_port_manifest().top_level_modules` listesini `--limit` ile yazar

Kaynaklar:
- [src/main.py#L98](/home/eren/Desktop/claw-code/src/main.py#L98)
- [src/main.py#L101](/home/eren/Desktop/claw-code/src/main.py#L101)
- [src/main.py#L104](/home/eren/Desktop/claw-code/src/main.py#L104)
- [src/main.py#L107](/home/eren/Desktop/claw-code/src/main.py#L107)
- [src/main.py#L110](/home/eren/Desktop/claw-code/src/main.py#L110)
- [src/main.py#L113](/home/eren/Desktop/claw-code/src/main.py#L113)
- [src/main.py#L116](/home/eren/Desktop/claw-code/src/main.py#L116)
- [src/main.py#L119](/home/eren/Desktop/claw-code/src/main.py#L119)

### Snapshot Yuzeyi Komutlari

- `commands`:
  `--query` varsa `render_command_index()` cagrilir.
  `--query` yoksa `get_commands()` cagrilir.
  `--no-plugin-commands` ve `--no-skill-commands` filtre olarak kullanilir.

- `tools`:
  `--query` varsa `render_tool_index()` cagrilir.
  `--query` yoksa `ToolPermissionContext.from_iterables(...)` ile permission context kurulur ve `get_tools(...)` cagrilir.
  `--simple-mode`, `--no-mcp`, `--deny-tool`, `--deny-prefix` burada kullanilir.

Kaynaklar:
- [src/main.py#L34](/home/eren/Desktop/claw-code/src/main.py#L34)
- [src/main.py#L40](/home/eren/Desktop/claw-code/src/main.py#L40)
- [src/main.py#L123](/home/eren/Desktop/claw-code/src/main.py#L123)
- [src/main.py#L132](/home/eren/Desktop/claw-code/src/main.py#L132)

### Runtime Benzeri Komutlar

- `route`: `PortRuntime().route_prompt(args.prompt, limit=args.limit)`
- `bootstrap`: `PortRuntime().bootstrap_session(args.prompt, limit=args.limit).as_markdown()`
- `turn-loop`: `PortRuntime().run_turn_loop(...)`
- `flush-transcript`: `QueryEnginePort.from_workspace()`, `submit_message()`, `persist_session()`
- `load-session`: `load_session(args.session_id)`

Kaynaklar:
- [src/main.py#L142](/home/eren/Desktop/claw-code/src/main.py#L142)
- [src/main.py#L150](/home/eren/Desktop/claw-code/src/main.py#L150)
- [src/main.py#L153](/home/eren/Desktop/claw-code/src/main.py#L153)
- [src/main.py#L160](/home/eren/Desktop/claw-code/src/main.py#L160)
- [src/main.py#L167](/home/eren/Desktop/claw-code/src/main.py#L167)

### Mode Komutlari

- `remote-mode`: `run_remote_mode(args.target).as_text()`
- `ssh-mode`: `run_ssh_mode(args.target).as_text()`
- `teleport-mode`: `run_teleport_mode(args.target).as_text()`
- `direct-connect-mode`: `run_direct_connect(args.target).as_text()`
- `deep-link-mode`: `run_deep_link(args.target).as_text()`

Kaynaklar:
- [src/main.py#L171](/home/eren/Desktop/claw-code/src/main.py#L171)
- [src/main.py#L174](/home/eren/Desktop/claw-code/src/main.py#L174)
- [src/main.py#L177](/home/eren/Desktop/claw-code/src/main.py#L177)
- [src/main.py#L180](/home/eren/Desktop/claw-code/src/main.py#L180)
- [src/main.py#L183](/home/eren/Desktop/claw-code/src/main.py#L183)

### Tekil Gosterim ve Shim Komutlari

- `show-command`: `get_command(args.name)`
- `show-tool`: `get_tool(args.name)`
- `exec-command`: `execute_command(args.name, args.prompt)`
- `exec-tool`: `execute_tool(args.name, args.payload)`

Kaynaklar:
- [src/main.py#L186](/home/eren/Desktop/claw-code/src/main.py#L186)
- [src/main.py#L193](/home/eren/Desktop/claw-code/src/main.py#L193)
- [src/main.py#L200](/home/eren/Desktop/claw-code/src/main.py#L200)
- [src/main.py#L204](/home/eren/Desktop/claw-code/src/main.py#L204)

## Arguman Alan Komutlar

Pozisyonel arguman alan komutlar:
- `route`: `prompt`
- `bootstrap`: `prompt`
- `turn-loop`: `prompt`
- `flush-transcript`: `prompt`
- `load-session`: `session_id`
- `remote-mode`: `target`
- `ssh-mode`: `target`
- `teleport-mode`: `target`
- `direct-connect-mode`: `target`
- `deep-link-mode`: `target`
- `show-command`: `name`
- `show-tool`: `name`
- `exec-command`: `name`, `prompt`
- `exec-tool`: `name`, `payload`

Kaynak:
- [src/main.py#L31](/home/eren/Desktop/claw-code/src/main.py#L31)

## Komut Sayisi

`src/main.py` icinde toplam 22 adet subcommand tanimi vardir.

Kaynak:
- [src/main.py#L24](/home/eren/Desktop/claw-code/src/main.py#L24)
