---
title: 'Gewusst wie: Ausführen der Codeanalyse manuell für verwalteten Code'
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431383"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Gewusst wie: Ausführen der Codeanalyse manuell für verwalteten Code (erfordert Visual Studio 2019 Version 16.5 oder höher)
Standardmäßig analysieren .NET Compiler Platform ("Roslyn")-Codeanalysatoren Ihren C- oder Visual Basic-Code während der Eingabe durch Live-Analysen sowie während des Builds. Daher müssten Sie normalerweise keine Codeanalyse manuell auslösen. Es gibt jedoch einige Szenarien, in denen Sie die Codeanalyse manuell auslösen möchten:

- Standardmäßig führt die Livecodeanalyse Analysatoren nur für geöffnete Dateien in Visual Studio aus. Möglicherweise möchten Sie jedoch Codeanalysewarnungen für alle Dateien in einem bestimmten Projekt oder einer bestimmten Projektmappe anzeigen. Wenn dies der Fall ist, sollten Sie die Codeanalyse einmal für ein Projekt oder eine Projektmappe auslösen. Alternativ können Sie die kontinuierliche Livecodeanalyse für die gesamte Lösung aktivieren. Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren des Livecodeanalysebereichs für verwalteten Code](./configure-live-code-analysis-scope-managed-code.md).
- Sie können den Ausführungsworkflow für die Bedarfscodeanalyse einer kontinuierlichen Liveanalyse oder Buildzeitanalyse vorziehen. Wenn dies der Zutun hat, können Sie die Analyzer-Ausführung während der Live-Analyse und/oder beim Erstellen deaktivieren. Informationen zum Deaktivieren der Analyse finden Sie unter [Deaktivieren der Quellcodeanalyse](disable-code-analysis.md). Dann sollten Sie die Codeanalyse einmal für ein Projekt oder eine Projektmappe manuell auslösen. 

### <a name="run-code-analysis-manually"></a>Manuelles Ausführen der Codeanalyse

1. Klicken Sie im **Projektmappen-Explorer**auf das Projekt.

2. Klicken Sie im Menü **Analysieren** auf **Codeanalyse für** *Projektname*ausführen .

Die Codeanalyse beginnt im Hintergrund. Die Meldung Ausführen der **Codeanalyse \<für>...** in der Visual Studio-Statusleiste in der linken unteren Ecke. Sobald die Codeanalyse abgeschlossen ist, ändert sich die Statusmeldung in **Codeanalyse, \< **die für die Projekt->abgeschlossen ist. Die Fehlerliste wird in Kürze mit allen Diagnosen für die Codeanalyse aktualisiert.
