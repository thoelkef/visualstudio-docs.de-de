---
title: "CA2228: Nicht freigegebene Ressourcenformate nicht ver&#246;ffentlichen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotShipUnreleasedResourceFormats"
  - "CA2228"
helpviewer_keywords: 
  - "CA2228"
  - "DoNotShipUnreleasedResourceFormats"
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2228: Nicht freigegebene Ressourcenformate nicht ver&#246;ffentlichen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotShipUnreleasedResourceFormats|  
|CheckId|CA2228|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Ressourcendatei wurde mit einer Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] erstellt, die derzeit nicht unterstützt wird.  
  
## Regelbeschreibung  
 Ressourcendateien, die mithilfe von Vorabversionen von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] erstellt wurden, können von den unterstützten Versionen von .NET Framework eventuell nicht verwendet werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, erstellen Sie die Ressource mit einer unterstützten Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.