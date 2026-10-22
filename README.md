# unity.libsodium

## lcgame 主干维护

本仓库是 [netpyoung/unity.libsodium](https://github.com/netpyoung/unity.libsodium) 的修复 fork。全部自有修复、维护和文档提交集中在 [`master`](https://github.com/lcgamedevelop/unity.libsodium/tree/master)，GitHub 默认页、本地检出和项目包依赖统一使用该主干。每次修改前先同步最新上游，并核对自有修复；每次修改都在同次提交中更新本 README，记录日期、原因、最终修正和实际验证结果。

当前已同步上游 [`master`（`142cf335`）](https://github.com/netpyoung/unity.libsodium/commit/142cf3359b88b74f7a49ce5140abc6513d7614f9)，UPM 包版本为 **0.2.5**，原生库版本为 **libsodium 1.0.20-RELEASE**，包路径为 `LocalPackage`。上游原有的 `dev` 分支仅跟踪上游；额外自建分支在提交完整纳入主干后删除。

### 维护记录

| 日期 | 修改 | 验证与影响范围 |
| --- | --- | --- |
| 2026-10-22 | [保留 iOS 稳定版绑定修复](https://github.com/lcgamedevelop/unity.libsodium/commit/9eb55520657f37c9e5bf141dec07e4b99cbc128d)：在 `LocalPackage/Runtime/NativeLibsodium.cs` 移除 ed25519/ristretto255 各自的 `from_string`、`from_string_ro`、`scalar_is_canonical` 六项未导出声明。 | 静态核对剩余 642 个 P/Invoke，保留上游 WebGL 宏；全部原生库与上游一致。Windows 原生初始化、加解密、篡改拒绝检查通过；本次未重跑 iOS 真机测试。 |
| 2026-10-22 | [核对 Android ARMv7 修复已由上游包含](https://github.com/lcgamedevelop/unity.libsodium/commit/870df969621d801eca7b5e1889618e0c16713e28)：直接采用上游 0.2.5 的 `LocalPackage/Plugins/Android/libs/armeabi-v7a/libsodium.so.meta`，无需重复修改。 | 与上游文件逐字节一致，Any Platform、Editor、桌面和 iOS 均禁用，Android 启用且 CPU 为 ARMv7；GUID 与原生库不变。 |
| 2026-10-22 | 整理主干维护规则、README 记录与 `LocalPackage#master` 安装入口；以最新上游为基线，保留三条线性维护提交。 | 核对包版本为 0.2.5、上游提交完整包含，差异仅为 iOS 六项绑定移除及 README；清理额外自建分支，保留上游原有分支。 |

## What's this?

 I decided that there should be a simpler way and I created **unity.libsodium**, a plugin that helps you to use [libsodium](https://github.com/jedisct1/libsodium/) in your Unity3d projects in a clear and easy way and works in **iOS, Android, OSX, Windows, WebGL** projects.

## prebuilt library

- prebuilt library are maintained by [prebuilt-libsodium](https://github.com/netpyoung/prebuilt-libsodium)
  - libsodium 1.0.20-RELEASE

## installation

### using UPM

使用本 fork 的主干：

``` json
"com.netpyoung.libsodium": "https://github.com/lcgamedevelop/unity.libsodium.git?path=LocalPackage#master"
```

由 Unity Package Manager 解析并更新 `packages-lock.json`，用锁文件记录实际使用的提交；更新修复时重新解析主干并验证。

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
