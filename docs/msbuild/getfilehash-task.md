---
title: GetFileHash-Aufgabe | Microsoft-Dokumentation
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71ebd50b42408dc7bd2642c257dece686245870f
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2019
ms.locfileid: "55485041"
---
# <a name="getfilehash-task"></a>GetFileHash-Aufgabe

Berechnet Prüfsummen der Inhalte einer Datei oder mehrerer Dateien.

Diese Aufgabe wurde in Version 15.8 hinzugefügt, für die Verwendung für MSBuild-Versionen unter Version 16.0 ist jedoch ein [Workaround](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) erforderlich.

## <a name="task-parameters"></a>Aufgabenparameter

 In der folgenden Tabelle werden die Parameter der `GetFileHash` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Files`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br />Die Dateien, die gehasht werden sollen.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]`-Ausgabeparameter.<br /><br />Die `Files`-Eingabe mit zusätzlichen Metadaten für den Dateihash.|
|`Hash`|`String`-Ausgabeparameter.<br /><br />Der Hash der Datei. Diese Ausgabe wird nur festgelegt, wenn genau ein Element übergeben wurde.|
|`Algorithm`|Optionaler `String` -Parameter.<br /><br />Der Algorithmus. Zulässige Werte: `SHA256`, `SHA384` und `SHA512`. Standard = `SHA256`.|
|`MetadataName`|Optionaler `String` -Parameter.<br /><br />Der Name der Metadaten, in denen der Hash in jedem Element gespeichert ist. Wird standardmäßig auf `FileHash` festgelegt.|
|`HashEncoding`|Optionaler `String` -Parameter.<br /><br />Die Codierung für die generierten Hashes. Wird standardmäßig auf `hex` festgelegt. Zulässige Werte: `hex` und `base64`.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Aufgabe `GetFileHash` verwendet, um die Prüfsumme der `FilesToHash`-Elemente zu ermitteln und auszugeben.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

[Aufgaben](../msbuild/msbuild-tasks.md)

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)