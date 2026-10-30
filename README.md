# WeAI offline TTS engine package

Downloadable engine for the WeAI WeChat assistant. The module APK ships only the loader; the
engine, native libraries and the acoustic model arrive as a release asset.

## Contract

`engine.dex` must expose:

```java
package dev.wechat.ai.tts;
public final class OfflineEngine {
    // raw little-endian PCM16, mono, 16 kHz, or null when synthesis is impossible
    public static byte[] synth(String modelDir, String text);
}
```

## Package layout

```
manifest.json           name, version, entry, model, sample_rate
engine.dex              Java shim implementing the contract above
libsherpa-onnx-jni.so   arm64-v8a
libonnxruntime.so       arm64-v8a
model.onnx              Chinese VITS / Matcha model
tokens.txt
```

## Install

Release asset `sherpa-onnx-zh-arm64.zip`. SHA-256 is published in the release notes and pinned in
the module's default download settings.
