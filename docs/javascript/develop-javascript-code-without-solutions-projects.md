---
title: Schreiben von JavaScript-Code in Visual Studio ohne Projektmappe oder Projekt
description: Visual Studio unterstützt die Erstellung von Code ohne Abhängigkeit von einer Projekt- oder Projektmappendatei.
ms.custom: ''
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 7d56030b78abe57c80d816881991b9819ed6456b
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924740"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Entwickeln von JavaScript- und TypeScript-Code in Visual Studio ohne Projektmappen oder Projekte

Mit Visual Studio 2017 wird die Möglichkeit eingeführt, [Code ohne Projekte oder Projektmappen zu entwickeln](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md). Dadurch können Sie einen Ordner mit Code öffnen und sofort mit umfassender Editor-Unterstützung wie IntelliSense, Suche, Refactoring, Debuggen und vielem mehr arbeiten.
Neben diesen Features unterstützen die Node.js-Tools für Visual Studio das Erstellen von TypeScript-Dateien, das Verwalten von NPM-Paketen sowie das Ausführen von NPM-Skripts.

Wählen Sie zum Einstieg auf der Startseite, die angezeigt wird, wenn Sie Visual Studio öffnen, die Option **Ordner öffnen** aus. Sie können auch in der Symbolleiste **Datei** > **Öffnen** > **Ordner** auswählen. Im Projektmappen-Explorer werden alle Dateien im Ordner angezeigt und Sie können die Dateien zum Bearbeiten öffnen. Im Hintergrund werden die Dateien indiziert, um NPM-Features und Features zum Kompilieren und Debuggen zu aktivieren.

> [!IMPORTANT]
> Für viele in diesem Artikel beschriebene Features ist Visual Studio 2017 Version 15.8 Preview 3 erforderlich, so auch für NPM-Integration.

## <a name="npm-integration"></a>NPM-Integration

Wenn der Ordner, den Sie öffnen, die Datei *package.json* enthält, können Sie mit der rechten Maustaste auf *package.json* klicken, um ein NPM-spezifisches Kontextmenü anzuzeigen. 

![NPM-Menü im Projektmappen-Explorer](../javascript/media/solution-explorer-npm-ctx.png) 

Im Kontextmenü können Sie die durch NPM installierten Pakete auf dieselbe Weise verwalten, wie Sie [NPM-Pakete mit einer Projektdatei verwalten](npm-package-management.md).

Ferner können Sie über das Menü auch Skripts ausführen, die im `scripts`-Element in *package.json* definiert sind. Für diese Skripts wird die Version von Node.js verwendet, die in der Umgebungsvariablen `PATH` verfügbar ist. Die Skripts werden in einem neuen Fenster ausgeführt. Dies ist eine hervorragende Möglichkeit, Skripts zu kompilieren oder auszuführen.

## <a name="build-and-debug"></a>Kompilieren und Debuggen

### <a name="packagejson"></a>package.json
Wenn die Datei *package.json* im Ordner ein `main`-Element angibt, ist der Befehl **Debuggen** im Kontextmenü für *package.json* verfügbar. Wenn Sie darauf klicken, wird *node.exe* mit dem angegebenen Skript als Argument ausgeführt.

### <a name="javascript-files"></a>JavaScript-Dateien
Sie können JavaScript-Dateien debuggen, indem Sie mit der rechten Maustaste auf eine Datei klicken und im Kontextmenü **Debuggen** auswählen. Dadurch wird *node.exe* mit der jeweiligen JavaScript-Datei als Argument ausgeführt.

### <a name="typescript-files-and-tsconfigjson"></a>TypeScript-Dateien und tsconfig.json
Wenn sich die Datei *tsconfig.json* nicht im Ordner befindet, können Sie mit der rechten Maustaste auf eine TypeScript-Datei klicken, um Kontextmenübefehle zum Kompilieren und Debuggen dieser Datei anzuzeigen. Wenn Sie diese Befehle verwenden, wird *tsc.exe* mit Standardoptionen verwendet. (Sie müssen die Datei zuerst kompilieren. Erst danach können Sie sie debuggen.)

> [!NOTE]
> Zum Kompilieren von TypeScript-Code verwenden wir die neueste Version, die in `C:\Program Files (x86)\Microsoft SDKs\TypeScript` installiert ist.

Wenn im Ordner die Datei *tsconfig.json* vorhanden ist, können Sie mit der rechten Maustaste auf eine TypeScript-Datei klicken, um den Menübefehl zum Debuggen dieser TypeScript-Datei anzuzeigen. Die Option wird nur angezeigt, wenn `outFile` in *tsconfig.json* nicht angegeben ist. Wenn `outFile` angegeben ist, können Sie diese Datei debuggen, indem Sie mit der rechten Maustaste auf *tsconfig.json* klicken und die entsprechende Option auswählen. Die `tsconfig.json`-Datei stellt zudem eine Option zum Kompilieren bereit, sodass Sie Compileroptionen festlegen können.

> [!NOTE]
> Weitere Informationen zu *tsconfig.json* finden Sie auf der Seite [tsconfig.json TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).
