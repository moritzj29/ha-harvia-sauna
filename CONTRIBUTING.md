# Contributing to Harvia Sauna Integration

Thanks for your interest in contributing! Here's how you can help.

## Translations

Translations are the easiest way to contribute. We currently support 19 languages and welcome improvements and additions.

### Fixing a translation

1. Edit the relevant file in `custom_components/harvia_sauna/translations/<lang>.json`
2. Submit a PR with your changes

### Adding a new language

1. Copy `custom_components/harvia_sauna/translations/en.json` to `<lang>.json` (use [BCP 47](https://www.iana.org/assignments/language-subtag-registry/) language tags, e.g. `pt-BR`, `zh-Hans`)
2. Translate all values (keep JSON keys unchanged)
3. Ensure all 57 keys are present — the CI will catch missing keys
4. Submit a PR

**Important:** Only native speakers should submit translations. Don't translate brand names (Harvia, MyHarvia, Xenio, Fenix).

## Bug Reports

Open an [issue](https://github.com/WiesiDeluxe/ha-harvia-sauna/issues) with:

- Your HA version and integration version
- Controller type (Xenio/Fenix) and heater model
- Steps to reproduce
- Relevant logs (Settings → System → Logs, filter for `harvia_sauna`)
- Diagnostics download if possible (Settings → Devices & Services → Harvia Sauna → ⋮ → Download diagnostics)

## Feature Requests

Open an issue describing what you'd like and why. If you have a Fenix controller, any testing feedback is especially valuable since the Fenix API support is still maturing.

## Code Contributions

1. Fork the repo and create a branch
2. Follow the existing code style (type hints, docstrings)
3. Test with your hardware if possible
4. Submit a PR against `main`

### Architecture overview

```
api_base.py          → Abstract API interface
api.py               → MyHarvia/Xenio client (Cognito + AppSync)
api_harviaio.py      → Harvia.io/Fenix client (REST + GraphQL)
api_factory.py       → Routes to correct client based on config
coordinator.py       → DataUpdateCoordinator with session tracking
websocket.py         → Xenio WebSocket subscriptions
websocket_harviaio.py → Fenix WebSocket subscriptions
```

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
