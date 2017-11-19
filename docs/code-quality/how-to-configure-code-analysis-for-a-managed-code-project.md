---
title: "Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d62957a75c844d736a1168010616d5cf2c795bee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Gewusst wie: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code
In [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] und [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], Sie können auswählen, aus einer Liste der Codeanalyse *-Regelsätze* um auf ein Projekt mit verwaltetem Code anzuwenden. Der Standardregelsatz sind die Microsoft-Mindestregeln. Sie können einen anderen Regelsatz auf ein Projekt oder alle Projekte in einer Projektmappe anwenden.  
  
> [!NOTE]
>  Informationen zum Konfigurieren eines Regelsatzes für ASP.NET-Webanwendungen finden Sie unter [Vorgehensweise: Konfigurieren der Codeanalyse für eine ASP.NET-Webanwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>So konfigurieren Sie einen Regelsatz für ein .NET Framework-Projekt  
  
1.  In **Projektmappen-Explorer**, klicken Sie auf das Projekt.  
  
2.  Auf der **analysieren** Menü klicken Sie auf **Konfigurieren der Codeanalyse für** *Projektname*.  
  
3.  In der **Konfiguration** und **Plattform** Listen, klicken Sie auf den Build und die Zielplattform.  
  
4.  Wählen Sie zum Ausführen der Codeanalyse jedes Mal, wenn das Projekt erstellt wird, mit der ausgewählten Konfiguration der **Codeanalyse für Build aktivieren (definiert eine CODE_ANALYSIS-Konstante)** Kontrollkästchen. Sie können Codeanalyse auch manuell ausführen, indem Sie öffnen die **analysieren** klicken und im Menü **Ausführen der Codeanalyse für** *Projektname*.  
  
5.  Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird. Um Warnungen zu generiertem Code anzuzeigen, deaktivieren Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.  
  
    > [!NOTE]
    >  Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.  
  
6.  In der **diesen Regelsatz ausführen** führen Sie eines der folgenden:  
  
    -   Wählen Sie den Regelsatz, den Sie verwenden möchten.  
  
    -   Klicken Sie auf  **\<durchsuchen... >** zu einer vorhandenen benutzerdefinierten Regelsatz anzugeben, ist nicht in der Liste.  
  
    -   Definieren Sie einen benutzerdefinierten Regelsatz.  
  
         Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)