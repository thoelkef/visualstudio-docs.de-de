---
title: "Gewusst wie: Angeben von Regels&#228;tzen f&#252;r verwalteten Code f&#252;r mehrere Projekte in einer Projektmappe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.solution"
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Gewusst wie: Angeben von Regels&#228;tzen f&#252;r verwalteten Code f&#252;r mehrere Projekte in einer Projektmappe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Standardmäßig wird allen verwalteten Projekten einer Projektmappe der Codeanalyse\-*Regelsatz* für empfohlene Microsoft\-Mindestregeln zugewiesen.  Sie können die Regelsätze ändern, die den Projekten einer Projektmappe im Eigenschaftendialogfeld für die Projektmappe zugewiesen werden.  
  
> [!NOTE]
>  Standardmäßig wird die Projektcodeanalyse nicht als Buildschritt ausgeführt.  Informationen zum Aktivieren der Codeanalyse als Buildschritt finden Sie unter [Gewusst wie: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### So geben Sie einen Regelsatz für mehrere Projekte in einer Projektmappe mit verwaltetem Code an  
  
1.  In [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  Öffnen Sie die Lösung in [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] oder [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)].  
  
2.  Klicken Sie im Menü **Analyse** auf **Codeanalyse für Projektmappe konfigurieren**.  
  
3.  Erweitern Sie ggf. **Allgemeine Eigenschaften**, und klicken Sie dann auf **Codeanalyseeinstellungen**.  
  
4.  Sie können einen Regelsatz für ein oder mehrere Projekte angeben.  
  
    -   Klicken Sie auf den Projektnamen, um einen Regelsatz für ein einzelnes Projekt anzugeben.  
  
    -   Halten Sie die STRG\-TASTE gedrückt, und klicken Sie auf die Projektnamen, um einen Regelsatz für mehrere Projekte anzugeben.  
  
    -   Halten Sie die UMSCHALTTASTE gedrückt, und klicken Sie in die Projektliste, um alle Projekte in der Projektmappe anzugeben.  
  
5.  Klicken Sie auf das Feld **Regelsatz** eines Projekts und dann auf den Namen des Regelsatzes, den Sie übernehmen möchten.