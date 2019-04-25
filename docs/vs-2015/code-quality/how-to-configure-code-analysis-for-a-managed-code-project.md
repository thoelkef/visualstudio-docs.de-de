---
title: 'Vorgehensweise: Codeanalyse für ein Projekt mit verwaltetem Code konfigurieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a326be363295ed1033d0e91e1675e326a51c9adf
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104316"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] und [!INCLUDE[vsPro](../includes/vspro-md.md)], können Sie aus einer Liste der Codeanalyse *-Regelsätze* um auf ein Projekt mit verwaltetem Code anzuwenden. Der Standardregelsatz sind die Microsoft-Mindestregeln. Sie können einen anderen Regelsatz auf ein Projekt oder alle Projekte in einer Projektmappe anwenden.  
  
> [!NOTE]
>  Informationen dazu, wie Sie einen Regelsatz für ASP.NET-Webanwendungen zu konfigurieren, finden Sie unter [Vorgehensweise: Konfigurieren der Codeanalyse für eine ASP.NET-Webanwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>So konfigurieren Sie einen Regelsatz für ein .NET Framework-Projekt  
  
1. In **Projektmappen-Explorer**, klicken Sie auf das Projekt.  
  
2. Auf der **analysieren** Menü klicken Sie auf **Konfigurieren der Codeanalyse für** *ProjectName*.  
  
3. In der **Konfiguration** und **Plattform** Listen, klicken Sie auf die Build-Konfiguration und die Zielplattform.  
  
4. Codeanalyse ausführen jedes Mal, wenn das Projekt mit der ausgewählten Konfiguration erstellt wird, wählen die **Codeanalyse für Build aktivieren (definiert eine CODE_ANALYSIS-Konstante)** Kontrollkästchen. Sie können die Codeanalyse auch manuell ausführen, indem Sie öffnen die **analysieren** klicken und im Menü **Ausführen der Codeanalyse für** *ProjectName*.  
  
5. Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird. Um Warnungen zu generiertem Code anzuzeigen, deaktivieren Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.  
  
    > [!NOTE]
    >  Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.  
  
6. In der **diesen Regelsatz ausführen** aufzulisten, führen Sie eine der folgenden:  
  
    - Wählen Sie den Regelsatz, den Sie verwenden möchten.  
  
    - Klicken Sie auf  **\<durchsuchen... >** einen vorhandenen benutzerdefinierten Regelsatz anzugeben, ist nicht in der Liste.  
  
    - Definieren Sie einen benutzerdefinierten Regelsatz.  
  
         Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Legen Sie die Konfiguration und Verwendung einer benutzerdefinierten Regelsatzes](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
