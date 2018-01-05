---
title: "Vorgehensweise: Konfigurieren der Codeanalyse für eine ASP.NET-Webanwendung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 51ece959ad0c33c4676e81203cacc025d9ef2884
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Gewusst wie: Konfigurieren der Codeanalyse für eine ASP.NET-Anwendung
In [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] und [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] aus einer Liste der Codeanalyse Auszuwählender *-Regelsätze* zuweisen [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Webanwendung. Der Standardregelsatz sind die Microsoft-Mindestregeln. Sie können einen anderen Regelsatz Zuweisen der Website auswählen.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>So konfigurieren Sie einen Regelsatz für ein ASP.NET-Seitenframeworkprojekt  
  
1.  Wählen Sie die Website im **Projektmappen-Explorer**.  
  
2.  Auf der **analysieren** Menü klicken Sie auf **Konfigurieren der Codeanalyse für Website**.  
  
3.  Wenn Sie die Lösung ausgewählt, und die Lösung mehr als ein Projekt bietet, wählen Sie den Build und Betriebssystem von der **Konfiguration** und **Plattform** aufgeführt.  
  
4.  Für jedes Projekt in der Projektmappe, klicken Sie auf die **Regelsatz** Spalte, und klicken Sie dann auf der Namen der Regel legen Sie auf ausführen.  
  
5.  Standardmäßig wird die Codeanalyse für alle Projekte in der Projektmappe ausgeführt. So deaktivieren oder aktivieren die Codeanalyse für ein bestimmtes Projekt, gehen Sie folgendermaßen vor:  
  
    1.  Maustaste auf den Projektnamen, und klicken Sie dann auf Eigenschaften.  
  
    2.  Aktivieren oder Deaktivieren der **Codeanalyse aktivieren** Kontrollkästchen. Sie können Codeanalyse auch manuell ausführen, indem Sie auswählen **Codeanalyse ausführen, auf der Website** aus der **analysieren** Menü.  
  
6.  In der **diesen Regelsatz ausführen** Dropdown-Liste, gehen Sie folgendermaßen vor:  
  
    -   Wählen Sie den Regelsatz, den Sie verwenden möchten.  
  
    -   Wählen Sie  **\<Durchsuchen >** zu einer vorhandenen benutzerdefinierten Regelsatz anzugeben, ist nicht in der Liste.  
  
    -   Definieren Sie einen benutzerdefinierten Regelsatz. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).