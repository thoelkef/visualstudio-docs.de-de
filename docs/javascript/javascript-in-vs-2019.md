---
title: JavaScript und TypeScript in Visual Studio 2019
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 199a27dbfef2b7297563e87d973137e2acd9c745
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544288"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript und TypeScript in Visual Studio 2019

## <a name="overview"></a>Übersicht

Visual Studio 2019 bietet umfangreiche Unterstützung für die JavaScript-Entwicklung, sowohl mit JavaScript direkt, als auch mit der Programmiersprache [TypeScript](http://www.typescriptlang.org/), die entwickelt wurde, um eine produktivere und angenehmere JavaScript-Entwicklung zu ermöglichen, insbesondere bei der Entwicklung von Projekten im großen Stil. Sie können JavaScript- oder TypeScript-Code in Visual Studio für viele Arten von Anwendungen und Dienste schreiben.

## <a name="javascript-language-service"></a>JavaScript-Sprachdienst

JavaScript in Visual Studio 2019 wird von der gleichen Engine unterstützt, die auch TypeScript unterstützt. Dadurch erhalten Sie sofort bessere Unterstützung, Vielfalt und Integration von Funktionen.

Die Option der Wiederherstellung in den veralteten JavaScript-Sprachdienst ist nicht mehr verfügbar. Benutzer verfügen jetzt von Anfang an über den neuen JavaScript-Sprachdienst. Der neue Sprachdienst basiert ausschließlich auf dem TypeScript-Sprachdienst, der auf statischer Analyse basiert. Dies ermöglicht eine bessere Verwendung von Tools, sodass Ihr JavaScript-Code vom umfangreicheren IntelliSense, basierend auf Typdefinitionen, profitieren kann. Der neue Dienst ist schlank und verbraucht weniger Speicher als der Legacydienst, bietet Ihnen aber gleichzeitig bessere Leistung, wenn Sie Code skalieren. Wir haben auch die Leistung des Sprachdienstes verbessert, um größere Projekte zu bearbeiten.

## <a name="typescript-support"></a>TypeScript-Unterstützung

Visual Studio 2019 bietet mehrere Optionen zur Integration der TypeScript-Kompilierung in Ihr Projekt:

* [Das TypeScript-NuGet-Paket](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Wenn das NuGet-Paket für TypeScript 3.2 oder höher in Ihrem Projekt installiert ist, wird die entsprechende Version des TypeScript-Sprachdienstes in den Editor geladen.
* [Das TypeScript-npm-Paket](https://www.npmjs.com/package/typescript). Wenn das npm-Paket für TypeScript 2.1 oder höher in Ihrem Projekt installiert ist, wird die entsprechende Version des TypeScript-Sprachdienstes in den Editor geladen.
* Das TypeScript SDK, das standardmäßig im Visual Studio-Installer verfügbar ist, sowie ein eigenständiger SDK-Download vom [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).

> [!TIP]
> Für Projekte, die in Visual Studio 2019 entwickelt wurden, empfehlen wir Ihnen, das TypeScript-NuGet- oder das TypeScript-npm-Paket für eine bessere Portabilität über verschiedene Plattformen und Umgebungen hinweg zu verwenden.

Ein gängiger Anwendungsfall für das NuGet-Paket ist die Kompilierung von TypeScript mithilfe der .NET Core-CLI. Das NuGet-Paket ist die einzige Möglichkeit zum Aktivieren der TypeScript-Kompilierung mit .NET Core-CLI-Befehlen wie `dotnet build` und `dotnet publish`, es sei denn, Sie bearbeiten Ihre Projektdatei manuell, um Buildziele von einer Installation der TypeScript SDK zu importieren.

## <a name="remove-default-imports-aspnet-core-projects"></a>Entfernen von Standardimporten (ASP.NET Core-Projekte)

Bei älteren Projekten, die ein [Nicht-SDK-Format](https://docs.microsoft.com/nuget/resources/check-project-format) verwenden, müssen Sie einige Projektdateielemente möglicherweise entfernen.

Wenn Sie das NuGet-Paket für MSBuild-Unterstützung in einem Projekt verwenden, darf die Projektdatei weder `Microsoft.TypeScript.Default.props` noch `Microsoft.TypeScript.targets` importieren. Die Dateien werden vom NuGet-Paket importiert, d. h., wenn Sie sie separat einfügen, kann ein unerwartetes Verhalten auftreten.

1. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Projekt entladen** aus.

1. Klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **\<*Projektdateiname*\> bearbeiten** aus.

   Daraufhin wird die Projektdatei geöffnet.

1. Entfernen Sie die Verweise auf `Microsoft.TypeScript.Default.props` und `Microsoft.TypeScript.targets`.

   Die zu entfernenden Importe sehen etwa wie folgt aus:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```

## <a name="projects"></a>Projekte

UWP-JavaScript-Apps werden in Visual Studio 2019 nicht mehr unterstützt. Sie können keine JavaScript-UWP-Projekte erstellen oder öffnen (Dateien mit der Erweiterung *.jsproj*). Weitere Informationen finden Sie in unserer [Dokumentation zum Erstellen von progressiven Web-Apps (PWAs), die sich gut unter Windows ausführen lassen](/microsoft-edge/progressive-web-apps/get-started).
