---
title: "CA1719: Parameternamen sollten nicht Membernamen übereinstimmen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1fd1d1af9287b73d9d1f44143e6673d2a67b690c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen
|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Der Name eines extern sichtbaren Members übereinstimmt, in Groß-und Kleinschreibung unterschieden, den Namen einer seiner Parameter.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln. Diese stimmen in der Regel nicht überein. Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wählen Sie einen Parameternamen an, der den Membernamen nicht übereinstimmen.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Für neue Entwicklungen keine bekannten Szenarien auftreten, in dem Sie eine Warnung dieser Regel unterdrücken müssen. Für den Protokollversand Bibliotheken, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)