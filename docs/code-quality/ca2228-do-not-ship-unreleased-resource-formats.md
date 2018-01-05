---
title: "CA2228: Führen Sie nicht freigegebene Ressourcenformate | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dcbd6627e17a4dfe179f485a2439aaf04c1a01ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nicht freigegebene Ressourcenformate nicht veröffentlichen
|||  
|-|-|  
|TypeName|DoNotShipUnreleasedResourceFormats|  
|CheckId|CA2228|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Eine Ressourcendatei erstellt wurde, mit einer Version von den [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] , der derzeit nicht unterstützt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ressourcendateien, die erstellt wurden, mithilfe von Vorabversionen von der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] möglicherweise nicht von den unterstützten Versionen von .NET Framework verwendet werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, erstellen Sie die Ressource mit einer unterstützten Version von den [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.