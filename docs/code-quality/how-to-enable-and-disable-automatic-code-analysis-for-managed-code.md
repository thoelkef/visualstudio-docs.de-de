---
title: "Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse für verwalteten Code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 198047196ba6f58c69736ef67352267845047b52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse für verwalteten Code
Sie können die Codeanalyse ausgeführt vor jedem Build für ein Projekt mit verwaltetem Code konfigurieren. Verschiedene Code Analysis-Eigenschaften können Sie festlegen, für die einzelnen [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Konfiguration.  
  
### <a name="to-enable-or-disable-automatic-code-analysis"></a>So aktivieren oder Deaktivieren der automatischen Codeanalyse  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld "Eigenschaften" für das Projekt auf **Codeanalyse**.  
  
3.  Geben Sie den Build in **Konfiguration** und die Zielplattform in **Plattform**.  
  
4.  Klicken Sie zum Aktivieren oder Deaktivieren der automatischen Codeanalyse, aktivieren oder Deaktivieren der **Codeanalyse für Build aktivieren (definiert eine CODE_ANALYSIS-Konstante)** Kontrollkästchen.