# unity.libsodium

## lcgame 修复记录

| 日期 | 修改 | 验证 |
| --- | --- | --- |
| 2026-10-22 | 保留 iOS 稳定版绑定修复：在 `LocalPackage/Runtime/NativeLibsodium.cs` 移除 ed25519/ristretto255 各自的 `from_string`、`from_string_ro`、`scalar_is_canonical` 六项未导出声明。 | 静态核对剩余 642 个 P/Invoke，保留上游 WebGL 宏；全部原生库与上游一致。Windows 原生初始化、加解密、篡改拒绝检查通过；本次未重跑 iOS 真机测试。 |

| 2026-10-22 | 核对 Android ARMv7 修复：上游 0.2.5 已完整包含 Android-only/ARMv7 配置，直接采用 `LocalPackage/Plugins/Android/libs/armeabi-v7a/libsodium.so.meta`。 | 与上游文件逐字节一致，Any Platform、Editor、桌面和 iOS 均禁用，Android 启用且 CPU 为 ARMv7；GUID 与原生库不变。 |

## What's this?

 I decided that there should be a simpler way and I created **unity.libsodium**, a plugin that helps you to use [libsodium](https://github.com/jedisct1/libsodium/) in your Unity3d projects in a clear and easy way and works in **iOS, Android, OSX, Windows, WebGL** projects.

## prebuilt library

- prebuilt library are maintained by [prebuilt-libsodium](https://github.com/netpyoung/prebuilt-libsodium)
  - libsodium 1.0.20-RELEASE

## installation

### using UPM

using #{version} for versioning.

``` json
"com.netpyoung.libsodium": "https://github.com/netpyoung/unity.libsodium.git?path=LocalPackage#0.2.5"
```

## License

### [libsodium](https://github.com/jedisct1/libsodium/)

``` license
/*
 * ISC License
 *
 * Copyright (c) 2013-2018
 * Frank Denis <j at pureftpd dot org>
 *
 * Permission to use, copy, modify, and/or distribute this software for any
 * purpose with or without fee is hereby granted, provided that the above
 * copyright notice and this permission notice appear in all copies.
 *
 * THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
 * WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
 * MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
 * ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
 * WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
 * ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
 * OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
*/
```

## contributor

- [@netpyoung](https://github.com/netpyoung)
- [@Ekwav](https://github.com/Ekwav)

## Ref

- <https://github.com/jedisct1/libsodium/tree/master/src/libsodium/include/sodium/>
- <https://github.com/joshjdevl/libsodium-jni/blob/master/src/main/java/org/libsodium/jni/SodiumJNI.java>
- <https://github.com/terl/lazysodium-android>
- <https://github.com/adamcaudill/libsodium-net/blob/master/libsodium-net/SodiumLibrary.cs>
- <https://github.com/microsoft/ClangSharp>
