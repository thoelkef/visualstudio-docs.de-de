---
title: Neues in MSBuild 15 | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
caps.latest.revision: "23"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ae35bafc612b4fd7b76a06c47300fee4f35ce5ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="whats-new-in-msbuild-15"></a>Neues in MSBuild 15
MSBuild ist jetzt als Teil des [.NET Core SDK](https://www.microsoft.com/net/download/core) verfügbar und ermöglicht die Erstellung von .NET Core-Projekten unter Windows, macOS und Linux.  

## <a name="changed-path"></a>Geänderter Pfad
 MSBuild wird jetzt in einem Ordner unterhalb der einzelnen Versionen von Visual Studio installiert. Beispielsweise `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild`. Sie können MSBuild auch mit dem folgenden PowerShell-Modul suchen: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild wird nicht mehr im globalen Assemblycache installiert. Um programmgesteuert auf MSBuild zu verweisen, verwenden Sie NuGet-Pakete.

## <a name="changed-properties"></a>Geänderte Eigenschaften  
 Die folgenden MSBuild-Eigenschaften wurden aufgrund der neuen Versionsnummer aktualisiert.  

-   `MSBuildToolsVersion` für diese Version der Tools ist 15.0. Die Assemblyversion ist 15.1.0.0.

-   `MSBuildToolsPath` weist keinen festgelegten Speicherort mehr auf. Standardmäßig befindet er sich im Ordner „MSBuild\15.0\Bin“ relativ zum Visual Studio-Installationspfad. Der Visual Studio-Installationspfad kann jedoch zur Installationszeit geändert werden.

-   `ToolsVersion`-Werte werden nicht mehr in der Registrierung festgelegt.  

-   Die Eigenschaften `SDK35ToolsPath` und `SDK40ToolsPath` verweisen auf das .NET Framework SDK, das mit dieser Version von Visual Studio geliefert wird (beispielsweise 10.0A für die 4.X-Tools).  

## <a name="updates"></a>Updates
- Das [Project-Element](../msbuild/project-element-msbuild.md) verfügt über ein neues `SDK`-Attribut. Das `Xmlns`-Attribut ist zudem jetzt optional.
- Das [Item-Element](../msbuild/item-element-msbuild.md) verfügt außerhalb von Zielen über ein neues `Update`-Attribut. Auch die Einschränkung für das `Remove`-Attribut wurde entfernt.
- `Directory.Build.props` ist eine benutzerdefinierte Datei, die Anpassungen für Projekte unter einem Verzeichnis bereitstellt. Diese Datei wird automatisch aus Microsoft.Common.props importiert, wenn die Eigenschaft `ImportDirectoryBuildTargets` nicht auf **FALSE** festgelegt wird. `Directory.Build.targets` wird durch Microsoft.Common.targets importiert.
- Alle Metadaten mit einem Namen, der der aktuellen Liste der Attribute nicht widerspricht, können optional als Attribut ausgedrückt werden. Weitere Informationen finden Sie unter [Item-Element](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Neue Eigenschaftenfunktionen

- `EnsureTrailingSlash` fügt einem Pfad einen nachgestellten Schrägstrich hinzu, falls keiner vorhanden ist.
- `NormalizePath` kombiniert Pfadelemente und stellt sicher, dass die ausgegebene Zeichenfolge die richtigen Verzeichnistrennzeichen für das aktuelle Betriebssystem aufweist.
- `NormalizeDirectory` kombiniert Pfadelemente, sorgt für die Verwendung eines nachgestellten Schrägstrichs und stellt sicher, dass die ausgegebene Zeichenfolge die richtigen Verzeichnistrennzeichen für das aktuelle Betriebssystem aufweist.
- `GetPathOfFileAbove` gibt den Pfad der unmittelbar vorangehenden Datei zurück. Dies ist zum Aufruf von `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />` funktional äquivalent.

## <a name="see-also"></a>Siehe auch
[MSBuild](../msbuild/msbuild.md)
