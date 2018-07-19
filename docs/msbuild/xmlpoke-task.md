---
title: XmlPoke-Aufgabe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2fdd33968958c2f8423f16ae1ac964915fc12489
ms.sourcegitcommit: 0853338831925fc63398b49f21f457b39f3c0a12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2018
ms.locfileid: "39030415"
---
# <a name="xmlpoke-task"></a>XmlPoke-Aufgabe

Legt die Werte einer XML-Datei wie von der XPath-Abfrage angegeben fest

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `XmlPoke` -Aufgabe beschrieben.
  
|Parameter|Beschreibung |
|---------------|-----------------|
|`Namespaces`|Optionaler `String` -Parameter.<br /><br /> Gibt die Namespaces für die Präfixe von XPath-Abfragen an `Namespaces` ist ein XML-Ausschnitt, der aus `Namespace`-Elementen mit den Attributen `Prefix` und `Uri` besteht. Das Attribut `Prefix` gibt das Präfix an, das dem im `Uri`-Attribut angegebenen Namespace zugeordnet werden soll. Verwenden Sie kein leeres `Prefix`-Attribut.|
|`Query`|Optionaler `String` -Parameter.<br /><br /> Gibt die XPath-Abfrage an|
|`Value`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt den Wert an, der in den angegebenen Pfad eingefügt werden soll.|
|`XmlInputPath`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt die XML-Eingabe als Dateipfad an|

## <a name="remarks"></a>Hinweise

 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

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

## <a name="see-also"></a>Siehe auch

 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
