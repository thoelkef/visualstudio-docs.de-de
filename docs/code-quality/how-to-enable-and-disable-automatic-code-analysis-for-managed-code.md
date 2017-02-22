---
title: "Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse f&#252;r verwalteten Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse f&#252;r verwalteten Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Codeanalyse so konfigurieren, dass sie vor jeder Erstellung eines verwalteten Codeprojekts ausgeführt wird.  Sie können für jede [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Konfiguration unterschiedliche Codeanalyseeigenschaften festlegen.  
  
### So aktivieren oder deaktivieren Sie die automatische Codeanalyse  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie im Eigenschaftendialogfeld für das Projekt auf **Codeanalyse**.  
  
3.  Geben Sie unter **Konfiguration** den Buildtyp und unter **Plattform** die Zielplattform an.  
  
4.  Um die automatische Codeanalyse zu aktivieren oder zu deaktivieren, aktivieren bzw. deaktivieren Sie das Kontrollkästchen **Codeanalyse für Build aktivieren \(definiert eine CODE\_ANALYSIS\-Konstante\)**.