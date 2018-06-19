---
title: 'Vorgehensweise: Konfigurieren der Codeanalyse für eine ASP.NET-Webanwendung in Visual Studio'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: bb1adaf9e97a950c6e9c53b3734debf5588fe0b9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919948"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Gewusst wie: Konfigurieren der Codeanalyse für eine ASP.NET-Anwendung

In Visual Studio können Sie aus einer Liste der Codeanalyse auswählen *-Regelsätze* zuweisen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Webanwendung. Der Standardregelsatz sind die Microsoft-Mindestregeln. Sie können einen anderen Regelsatz Zuweisen der Website auswählen.

1. Wählen Sie die Website im **Projektmappen-Explorer**.

2. Auf der **analysieren** Menü klicken Sie auf **Konfigurieren der Codeanalyse für Website**.

3. Wenn Sie die Lösung ausgewählt, und die Lösung mehr als ein Projekt bietet, wählen Sie den Build und Betriebssystem von der **Konfiguration** und **Plattform** aufgeführt.

4. Für jedes Projekt in der Projektmappe, klicken Sie auf die **Regelsatz** Spalte, und klicken Sie dann auf der Namen der Regel legen Sie auf ausführen.

5. Standardmäßig wird die Codeanalyse für alle Projekte in der Projektmappe ausgeführt. So deaktivieren oder aktivieren die Codeanalyse für ein bestimmtes Projekt, gehen Sie folgendermaßen vor:

    1. Maustaste auf den Projektnamen, und klicken Sie dann auf Eigenschaften.

    2. Aktivieren oder Deaktivieren der **Codeanalyse aktivieren** Kontrollkästchen. Sie können Codeanalyse auch manuell ausführen, indem Sie auswählen **Codeanalyse ausführen, auf der Website** aus der **analysieren** Menü.

6. In der **diesen Regelsatz ausführen** Dropdown-Liste, gehen Sie folgendermaßen vor:

    - Wählen Sie den Regelsatz, den Sie verwenden möchten.

    - Wählen Sie  **\<Durchsuchen >** zu einer vorhandenen benutzerdefinierten Regelsatz anzugeben, ist nicht in der Liste.

    - Definieren einer [benutzerdefinierten Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md).