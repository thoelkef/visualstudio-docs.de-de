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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53819a642edcdf0419dd445ac32dbde8d14ffb22
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579522"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash-Aufgabe

Überprüft, ob die Datei mit dem erwarteten Dateihash übereinstimmt. Wenn der Hash nicht übereinstimmt, schlägt die Aufgabe fehl.

Diese Aufgabe wurde in Version 15.8 hinzugefügt, für die Verwendung für MSBuild-Versionen unter Version 16.0 ist jedoch ein [Workaround](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) erforderlich.

## <a name="task-parameters"></a>Aufgabenparameter

 In der folgenden Tabelle werden die Parameter der `VerifyFileHash` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`File`|Erforderlicher `String` -Parameter.<br /><br />Die Datei, für die Hashes generiert werden sollen und die überprüft werden soll.|
|`Hash`|Erforderlicher `String` -Parameter.<br /><br />Der erwartete Hash der Datei.|
|`Algorithm`|Optionaler `String`-Parameter.<br /><br />Der Algorithmus. Zulässige Werte: `SHA256`, `SHA384` und `SHA512`. Standard = `SHA256`.|
|`HashEncoding`|Optionaler `String`-Parameter.<br /><br />Die Codierung für die generierten Hashes. Wird standardmäßig auf `hex` festgelegt. Zulässige Werte: `hex` und `base64`.|

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

Bei MSBuild 16.5 und höheren Versionen können Sie die Warnung mithilfe des folgenden Codes zu einer Benachrichtigung herabstufen, wenn Sie nicht möchten, dass der Build fehlschlägt, wenn der Hash nicht übereinstimmt, beispielsweise wenn Sie den Hashvergleich als Bedingung für die Ablaufsteuerung verwenden:

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>Siehe auch

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
