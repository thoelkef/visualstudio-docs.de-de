---
title: "CA1721: Eigenschaftennamen sollten nicht Get-Methoden übereinstimmen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 91a280093d269797daa019b727bf2020462a0808
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen
|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Der Name des ein öffentlicher oder geschützter Member beginnt mit "Get" und entspricht, andernfalls den Namen einer öffentlichen oder geschützten-Eigenschaft. Ein Typ, der eine Methode, die Namen enthält "GetColor" und eine Eigenschaft mit dem Namen 'Color' beispielsweise verletzt diese Regel.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Get-Methoden und Eigenschaften sollten über Namen verfügen, die ihre Funktion klar zu unterscheiden.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die ist erforderlich, um eine neue Softwarebibliothek Informationen zu erhalten, zudem wird, dass die Bibliothek von einem Benutzer, Kenntnisse in der Entwicklung von verwaltetem Code hat.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Ändern Sie den Namen ein, sodass sie nicht den Namen einer Methode übereinstimmt, der mit "Get" vorangestellt ist.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
> [!NOTE]
>  Diese Warnung kann ausgeschlossen werden, die Get-Methode durch Implementieren der Schnittstelle IExtenderProvider-verursacht.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel enthält eine Methode und Eigenschaft, die diese Regel verletzen.  
  
 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)