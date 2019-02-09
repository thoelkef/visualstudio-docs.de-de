---
title: Konfigurieren der Codeanalyse für ASP.NET Web-app
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 51638db2cf258cc1a91c659c137c6a17811fa8c8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923838"
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