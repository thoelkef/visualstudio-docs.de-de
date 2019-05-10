---
title: JavaScript und TypeScript in Visual Studio 2019
ms.date: 03/27/2019
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
ms.openlocfilehash: 3000510c6bb6079629a3df05909417593569c932
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553254"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript und TypeScript in Visual Studio 2019

## <a name="overview"></a>Übersicht

Visual Studio 2019 bietet umfangreiche Unterstützung für die JavaScript-Entwicklung, sowohl mit JavaScript direkt, als auch mit der Programmiersprache [TypeScript](http://www.typescriptlang.org), die entwickelt wurde, um eine produktivere und angenehmere JavaScript-Entwicklung zu ermöglichen, insbesondere bei der Entwicklung von Projekten im großen Stil. Sie können JavaScript- oder TypeScript-Code in Visual Studio für viele Arten von Anwendungen und Dienste schreiben.

## <a name="javascript-language-service"></a>JavaScript-Sprachdienst

JavaScript in Visual Studio 2019 wird von der gleichen Engine unterstützt, die auch TypeScript unterstützt. Dadurch erhalten Sie sofort bessere Unterstützung, Vielfalt und Integration von Funktionen.

Die Option der Wiederherstellung in den veralteten JavaScript-Sprachdienst ist nicht mehr verfügbar. Benutzer verfügen jetzt von Anfang an über den neuen JavaScript-Sprachdienst. Der neue Sprachdienst basiert ausschließlich auf dem TypeScript-Sprachdienst, der auf statischer Analyse basiert. Dies ermöglicht eine bessere Verwendung von Tools, sodass Ihr JavaScript-Code vom umfangreicheren IntelliSense, basierend auf Typdefinitionen, profitieren kann. Der neue Dienst ist schlank und verbraucht weniger Speicher als der Legacydienst, bietet Ihnen aber gleichzeitig bessere Leistung, wenn Sie Code skalieren. Wir haben auch die Leistung des Sprachdienstes verbessert, um größere Projekte zu bearbeiten.

## <a name="typescript-support"></a>TypeScript-Unterstützung

Visual Studio 2019 bietet mehrere Optionen zur Integration der TypeScript-Kompilierung in Ihr Projekt:

* [Das TypeScript-NuGet-Paket](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Wenn das NuGet-Paket für TypeScript 3.2 oder höher in Ihrem Projekt installiert ist, wird die entsprechende Version des TypeScript-Sprachdienstes in den Editor geladen.
* Das TypeScript SDK, das standardmäßig im Visual Studio-Installer verfügbar ist, sowie ein eigenständiger SDK-Download vom [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).
* [Das TypeScript-npm-Paket](https://www.npmjs.com/package/typescript). Wenn das npm-Paket für TypeScript 2.1 oder höher in Ihrem Projekt installiert ist, wird die entsprechende Version des TypeScript-Sprachdienstes in den Editor geladen.

Für Projekte, die in Visual Studio 2019 entwickelt wurden, empfehlen wir Ihnen, die TypeScript-NuGet- und -npm-Pakete für eine bessere Portabilität über verschiedene Plattformen und Umgebungen zu verwenden.

## <a name="projects"></a>Projekte

UWP-JavaScript-Apps werden in Visual Studio 2019 nicht mehr unterstützt. Sie können keine JavaScript-UWP-Projekte erstellen oder öffnen (Dateien mit der Erweiterung *.jsproj*). Weitere Informationen finden Sie in unserer [Dokumentation zum Erstellen von progressiven Web-Apps (PWAs), die sich gut unter Windows ausführen lassen](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/get-started).
