---
title: XmlPoke-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f44ce4736900fde35716ca3ec9dabb2d55c6df51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588381"
---
# <a name="xmlpoke-task"></a>XmlPoke-Aufgabe

Legt die Werte einer XML-Datei wie von der XPath-Abfrage angegeben fest

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `XmlPoke`-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Namespaces`|Optionaler `String`-Parameter.<br /><br /> Gibt die Namespaces für die Präfixe von XPath-Abfragen an `Namespaces` ist ein XML-Ausschnitt, der aus `Namespace`-Elementen mit den Attributen `Prefix` und `Uri` besteht. Das Attribut `Prefix` gibt das Präfix an, das dem im `Uri`-Attribut angegebenen Namespace zugeordnet werden soll. Verwenden Sie kein leeres `Prefix`-Attribut.|
|`Query`|Optionaler `String`-Parameter.<br /><br /> Gibt die XPath-Abfrage an|
|`Value`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt den Wert an, der in den angegebenen Pfad eingefügt werden soll.|
|`XmlInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt die XML-Eingabe als Dateipfad an|

## <a name="remarks"></a>Bemerkungen

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

Dies ist ein einfach zu bearbeitender sample.xml-Code:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

Wenn Sie in diesem Beispiel `/Package/mp:PhoneIdentity/PhonePublisherId` ändern möchten, gehen Sie folgendermaßen vor:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` wird hier als künstliches Namespacepräfix für den Standardnamespace verwendet.

## <a name="see-also"></a>Weitere Informationen

- [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
