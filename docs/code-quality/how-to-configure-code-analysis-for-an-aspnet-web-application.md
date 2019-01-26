---
title: Konfigurieren der Codeanalyse für ASP.NET Web-app
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 1483ba4ea8e726ed61dc7c65ec486d420dbeb8a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021935"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Vorgehensweise: Konfigurieren der Codeanalyse für eine ASP.NET-Webanwendung

In Visual Studio können Sie wählen aus einer Liste der Codeanalyse *-Regelsätze* zuweisen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web-Anwendung. Der Standardregelsatz sind die Microsoft-Mindestregeln. Sie können einen anderen Regelsatz zuweisen, die Website auswählen.

1. Wählen Sie die Website in **Projektmappen-Explorer**.

2. Auf der **analysieren** Menü klicken Sie auf **Codeanalyse für Website konfigurieren**.

3. Wenn Sie die Lösung ausgewählt, und die Lösung besteht aus mehr als ein Projekt, wählen Sie die Build-Konfiguration und Ziel-Betriebssystem aus der **Konfiguration** und **Plattform** aufgeführt.

4. Für jedes Projekt in der Projektmappe, klicken Sie auf die **Regelsatz** Spalte, und klicken Sie dann auf der Namen der Regel legen Sie zum Ausführen.

5. Standardmäßig wird die Codeanalyse auf alle Projekte in der Projektmappe ausgeführt. Zum Deaktivieren oder aktivieren die Codeanalyse für ein bestimmtes Projekt, gehen Sie folgendermaßen vor:

    1. Mit der rechten Maustaste in des Namens des Projekts, und klicken Sie dann auf Eigenschaften.

    2. Aktivieren oder Deaktivieren der **Codeanalyse aktivieren** Kontrollkästchen. Sie können die Codeanalyse auch manuell ausführen, indem Sie auswählen **Codeanalyse auf Website ausführen** aus der **analysieren** Menü.

6. In der **diesen Regelsatz ausführen** Dropdown-Liste, gehen Sie folgendermaßen vor:

    - Wählen Sie den Regelsatz, den Sie verwenden möchten.

    - Wählen Sie  **\<Durchsuchen >** einen vorhandenen benutzerdefinierten Regelsatz anzugeben, ist nicht in der Liste.

    - Definieren einer [benutzerdefinierten Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md).