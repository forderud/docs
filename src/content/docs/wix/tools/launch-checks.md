---
sidebar_position: 91
---

# How To: Block installation on missing or too old VCREDIST

It is sometimes desirable to block installation of an application if the Microsoft Visual C++ Redistributable is either missing or too old. The following sample demonstrates how block installation if the Microsoft Visual C++ 2015-2022 (x64) Redistributable is either missing or predates the 17.2 version.

```xml
<!-- Minimum version obtained by downloading "Visual C++ Redistributable for Visual Studio 2022" (x64) 17.2 from https://my.visualstudio.com/Downloads and checking the EXE file version. -->
<Upgrade Id="36F68A90-239C-34DF-B58C-64B30153CE35">
    <UpgradeVersion OnlyDetect="yes" Property="VCREDIST_X64" Minimum="14.32.31332.0" />
</Upgrade>
<Launch Condition="Installed OR VCREDIST_X64" Message="Microsoft Visual C++ 2015-2022 (x64) Redistributable missing or too old." />
```

Where `36F68A90-239C-34DF-B58C-64B30153CE35` is the UpgradeCode associated with the Microsoft Visual C++ 2015-2022 (x64) Redistributable.
