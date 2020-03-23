---
title: 'Gewusst wie: Ausführen der Legacycodeanalyse manuell für verwalteten Code'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432084"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Gewusst wie: Ausführen der Legacycodeanalyse manuell für verwalteten Code
Das Codeanalysetool informiert Sie über mögliche Fehler im Quellcode. Sie können die Codeanalyse bei jedem Build eines Codeprojekts automatisch ausführen und die Codeanalyse auch manuell ausführen. Die Regeln, die beim Ausführen der Codeanalyse überprüft werden, werden auf der Seite Codeanalyse der Projekteigenschaftenseiten angegeben. Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren der Codeanalyse für ein Verwaltetes Codeprojekt](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>So führen Sie die Codeanalyse manuell aus

1. Wenn Sie Visual Studio 2019 Version 16.5 oder höher haben, führen Sie den folgenden Befehl für die Eingabeaufforderung aus, bevor Sie Visual Studio starten:

```
set EnableLegacyCodeAnalysis = true
```

2. Klicken Sie im **Projektmappen-Explorer**auf das Projekt.

3. Klicken Sie im Menü **Analysieren** auf **Codeanalyse für** *Projektname*ausführen .

