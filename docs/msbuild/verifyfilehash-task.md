---
title: VerifyFileHash-Aufgabe | Microsoft-Dokumentation
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8122f1a3869efe32d7ae35ff05cdbb77ad84375
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2019
ms.locfileid: "55485048"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash-Aufgabe

Überprüft, ob die Datei mit dem erwarteten Dateihash übereinstimmt.

Diese Aufgabe wurde in Version 15.8 hinzugefügt, für die Verwendung für MSBuild-Versionen unter Version 16.0 ist jedoch ein [Workaround](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) erforderlich.

## <a name="task-parameters"></a>Aufgabenparameter

 In der folgenden Tabelle werden die Parameter der `VerifyFileHash` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`File`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br />Die Dateien, die gehasht und überprüft werden sollen.|
|`Hash`|Erforderlicher `String` -Parameter.<br /><br />Der erwartete Hash der Datei.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]`-Ausgabeparameter.<br /><br />Die `Files`-Eingabe mit zusätzlichen Metadaten für den Dateihash.|
|`Algorithm`|Optionaler `String` -Parameter.<br /><br />Der Algorithmus. Zulässige Werte: `SHA256`, `SHA384` und `SHA512`. Standard = `SHA256`.|
|`HashEncoding`|Optionaler `String` -Parameter.<br /><br />Die Codierung für die generierten Hashes. Wird standardmäßig auf `hex` festgelegt. Zulässige Werte: `hex` und `base64`.|

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Aufgabe `VerifyFileHash` verwenden, um dessen eigene Prüfsumme zu überprüfen.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch

[Aufgaben](../msbuild/msbuild-tasks.md)

[Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)