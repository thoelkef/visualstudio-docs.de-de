---
title: MSBuild-Bedingungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 926c54be9d31a6d0708b33248b6887c0ac7e324e
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184067"
---
# <a name="msbuild-conditions"></a>MSBuild-Bedingungen

MSBuild unterstützt bestimmte Bedingungen, die angewendet werden können, wenn ein `Condition`-Attribut zulässig ist. Diese Bedingungen sind in der folgenden Tabelle angegeben.

|Bedingung|Beschreibung|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Ergibt `true`, wenn `stringA` gleich `stringB`.<br /><br /> Zum Beispiel:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich. Bei dieser Überprüfung wird die Groß-/Kleinschreibung nicht berücksichtigt.|
|'`stringA`' != '`stringB`'|Ergibt `true`, wenn `stringA` ungleich `stringB`.<br /><br /> Zum Beispiel:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich. Bei dieser Überprüfung wird die Groß-/Kleinschreibung nicht berücksichtigt.|
|\<, >, \<=, >=|Wertet die numerischen Werte der Operanden aus. Gibt `true` aus, wenn die relationale Auswertung TRUE ist. Die Auswertung von Operanden muss eine dezimale oder hexadezimale Zahl ergeben. Hexadezimale Zahlen müssen mit „0x“ beginnen. **Hinweis**:  Im XML müssen die Zeichen `<` und `>` mit Escapezeichen versehen werden. Das Symbol `<` wird als `&lt;` dargestellt. Das Symbol `>` wird als `&gt;` dargestellt.|
|Exists('`stringA`')|Ergibt `true`, wenn eine Datei oder ein Ordner mit dem Namen `stringA` vorhanden ist.<br /><br /> Zum Beispiel:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|
|HasTrailingSlash('`stringA`')|Ergibt `true`, wenn die angegebene Zeichenfolge entweder einen nachgestellten umgekehrten Schrägstrich (\\) oder einen Schrägstrich (/) enthält.<br /><br /> Zum Beispiel:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|
|!|Ergibt `true`, wenn die Auswertung des Operanden `false` ergibt.|
|`And`|Ergibt `true`, wenn die Auswertung beider Operanden `true` ergibt.|
|`Or`|Ergibt `true`, wenn die Auswertung von mindestens einem Operanden `true` ergibt.|
|()|Gruppierungsmechanismus, dessen Auswertung `true` ergibt, wenn die Auswertung der darin enthaltenen Ausdrücke `true` ergibt.|
|$if$ ( %expression% ), $else$, $endif$|Überprüft, ob das angegebene `%expression%` dem Zeichenfolgenwert des übergebenen benutzerdefinierten Vorlagenparameters entspricht. Wenn die Auswertung der `$if$`-Bedingung `true` ergibt, werden die jeweiligen Anweisungen ausgeführt. Andernfalls wird die `$else$`-Bedingung überprüft. Wenn die Auswertung der `$else$`-Bedingung `true` ergibt, werden die jeweiligen Anweisungen ausgeführt. Andernfalls beendet die `$endif$`-Bedingung die Auswertung des Ausdrucks.<br /><br /> Anwendungsbeispiele finden Sie unter [Visual Studio project/item template parameter logic (Visual Studio-Projekt: Parameterlogik in Elementvorlagen)](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Sie können Zeichenfolgenmethoden in Bedingungen wie im folgenden Beispiel gezeigt verwenden, bei der die [TrimEnd()](/dotnet/api/system.string.trimend)-Funktion zum Vergleichen des relevanten Teils der Zeichenfolge verwendet wird, um zwischen .NET Framework- und .NET Core-Zielframeworks zu unterscheiden.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789.`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Siehe auch

- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Bedingte Konstrukte](../msbuild/msbuild-conditional-constructs.md)
- [Exemplarische Vorgehensweise: Erstellen einer neuen MSBuild-Projektdatei](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
