---
title: 'Vorgehensweise: Angeben von Regelsätzen für verwalteten Code für mehrere Projekte in einer Projektmappe | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d2469491eeb5419c70e208bbf6e1ed7809657dbc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218691"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Gewusst wie: Angeben von Regelsätzen für verwalteten Code für mehrere Projekte in einer Projektmappe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Standardmäßig werden alle verwalteten Projekten einer Projektmappe die Codeanalyse für die Microsoft-Mindestregeln zugewiesen *Regelsatz*. Sie können die Regelsätze ändern, die den Projekten einer Projektmappe im Eigenschaftendialogfeld für die Projektmappe zugewiesen werden.  
  
> [!NOTE]
>  Standardmäßig wird die Projektcodeanalyse nicht als Buildschritt ausgeführt. Zum Aktivieren der Codeanalyse als Buildschritt finden Sie unter [Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt für verwalteten Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>So geben Sie einen Regelsatz für mehrere Projekte in einer Projektmappe mit verwaltetem Code an  
  
1.  In [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. Öffnen Sie die Lösung in [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] oder [!INCLUDE[vsPro](../includes/vspro-md.md)].  
  
2.  Auf der **analysieren** Menü klicken Sie auf **Codeanalyse für Projektmappe konfigurieren**.  
  
3.  Erweitern Sie ggf. **allgemeine Eigenschaften**, und klicken Sie dann auf **Codeanalyseeinstellungen**.  
  
4.  Sie können einen Regelsatz für ein oder mehrere Projekte angeben.  
  
    -   Klicken Sie auf den Projektnamen, um einen Regelsatz für ein einzelnes Projekt anzugeben.  
  
    -   Halten Sie die STRG-TASTE gedrückt, und klicken Sie auf die Projektnamen, um einen Regelsatz für mehrere Projekte anzugeben.  
  
    -   Halten Sie die UMSCHALTTASTE gedrückt, und klicken Sie in die Projektliste, um alle Projekte in der Projektmappe anzugeben.  
  
5.  Klicken Sie auf die **Regelsatz** Feld eines Projekts und klicken Sie dann auf der Namen der Regel legen Sie, dass Sie anwenden möchten.



