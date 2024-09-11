---
title: APIs
contributors:
  - Toad
  - AssumedPseudonym
---

## Kobold Kare's Utilized computing APIs

Since late December, 2020, booting up Kobold Kare gives users the option of which computing API the program should use when booting up.
There are variations for the Windows and Mac versions, but the top KoboldKare option runs the default, recommended choice for each platform.

| API | Windows version | Macintosh version | Linux version | Creator | Links |
| --- | --- | --- | --- | --- | --- |
| Direct3D11  | Yes\*| No   | No   | Microsoft                     | [Wiki](https://en.wikipedia.org/wiki/Direct3D#Direct3D_11) \| [Website](https://www.khronos.org/vulkan/) |
| Vulkan      | Yes  | No   | Yes\*| Khronos Group                 | [Wiki](https://en.wikipedia.org/wiki/Vulkan_(API)) \| [Website](https://docs.microsoft.com/en-us/windows/win32/direct3d11/atoc-dx-graphics-direct3d-11) |
| GLCore      | Yes  | Yes  | Yes  | Silicon Graphics/Kronos Group | [Wiki](https://en.wikipedia.org/wiki/OpenGL) \| [Website](https://www.opengl.org/) |
| Metal       | No   | Yes\*| No   | Apple                         | [Wiki](https://en.wikipedia.org/wiki/Metal_(API)) \| [Website](https://developer.apple.com/metal/) |


\* The default, recommended API to run Kobold Kare

Since February 18, 2023, API has been restricted to their own platform in order to make compiling time faster  
[Source](https://github.com/naelstrof/KoboldKare/commit/33b9c2494c2730e8f87212ae62c3ae8a0819e11f#diff-f1db76edbe0068ccbe4382393c8275c49a9ec78927f9f82b29506a506049adea)