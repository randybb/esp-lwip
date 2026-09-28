# ESP-IDF v5.5.5 `lwip` component with mDNS-over-IPv6 fixes

This is ESP-IDF v5.5.5's `components/lwip`, with the lwIP submodule inlined at the
commit that ESP-IDF v5.5.5 pins (`c6f2f878`) plus the two commits from
[espressif/esp-lwip#94](https://github.com/espressif/esp-lwip/pull/94):

- `dns: Send IPv6 mDNS queries on the default netif`
- `dns: Prefer non-link-local AAAA answers`

It replaces the built-in component when it is added as a managed dependency named `lwip`.
In ESPHome:

```yaml
esp32:
  framework:
    type: esp-idf
    components:
      - name: lwip
        source: https://github.com/randybb/esp-lwip.git
        ref: idf-v5.5.5-lwip-component
        path: lwip
```

It only matches ESP-IDF v5.5.5 (`port/` and `Kconfig` are tied to the IDF release). Drop it
once the fix is part of the ESP-IDF version in use.
