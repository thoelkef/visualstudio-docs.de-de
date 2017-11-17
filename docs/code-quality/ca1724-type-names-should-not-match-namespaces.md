---
title: "CA1724: Typnamen sollten nicht mit übereinstimmen Namespaces | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 556fd9eee1bc453d4f9782459050367e18a3193b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen
|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Typname entspricht einem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Namespacenamen in Groß-und Kleinschreibung unterschieden.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Typnamen dürfen nicht mit den Namen von in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Klassenbibliothek definierten Namespaces übereinstimmen. Durch einen Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek eingeschränkt werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wählen Sie einen Namen, die nicht den Namen des empfängerserverzertifikats entspricht einem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Klassenbibliothek-Namespace.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Für neue Entwicklungen keine bekannten Szenarien auftreten, in dem Sie eine Warnung dieser Regel unterdrücken müssen. Bevor Sie die Warnung unterdrücken, sollten Sie sorgfältig, wie die Benutzer Ihrer Bibliothek mit dem übereinstimmenden Namen verwechselt werden können. Für den Protokollversand Bibliotheken, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.