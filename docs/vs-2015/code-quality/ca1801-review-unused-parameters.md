---
title: 'CA1801: Nicht verwendete Parameter überprüfen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0efbec121e08d026145d8762b574847fbd4a2b88
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143131"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Nicht verwendete Parameter überprüfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1801: Nicht verwendete Parameter überprüfen](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters).  
  
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn das Element nicht außerhalb der Assembly sichtbar ist müssen unabhängig von der Änderung.<br /><br /> Nicht unterbrechend – Wenn Sie ändern, dass das Element, um die Parameter innerhalb des Texts zu verwenden.<br /><br /> Wichtige – Wenn Sie den Parameter entfernen und außerhalb der Assembly sichtbar ist.|  
  
## <a name="cause"></a>Ursache  
 Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird. Diese Regel untersucht nicht die folgenden Methoden:  
  
- Methoden, die einen Delegaten auf.  
  
- Methoden, die als Ereignishandler verwendet werden.  
  
- Methoden deklariert werden, mit der `abstract` (`MustOverride` in Visual Basic) Modifizierer.  
  
- Methoden deklariert werden, mit der `virtual` (`Overridable` in Visual Basic) Modifizierer.  
  
- Methoden deklariert werden, mit der `override` (`Overrides` in Visual Basic) Modifizierer.  
  
- Methoden deklariert werden, mit der `extern` (`Declare` -Anweisung in Visual Basic) Modifizierer.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Überprüfen Sie die Parameter in nicht virtuellen Methoden, die nicht im Methodentext verwendet werden, um sicherzustellen, dass keine Richtigkeit Umfeld des Fehlers für den Zugriff darauf vorhanden ist. Nicht verwendete Parameter fallen Kosten für Wartung und Leistung.  
  
 Manchmal kann ein Verstoß gegen diese Regel auf einen Implementierungsfehler in der Methode hinweisen. Z. B. der Parameter sollte im Methodentext verwendet haben. Unterdrücken Sie Warnungen für diese Regel aus, wenn der Parameter aufgrund der Abwärtskompatibilität vorhanden sein muss.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den nicht verwendeten Parameter (eine fehlerhafte Änderung), oder verwenden Sie den Parameter im Methodentext (eine nicht unterbrechende Änderung).  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Es ist sicher eine Warnung dieser Regel für die zuvor abgelieferten Codes zu unterdrücken, für die die Lösung eine unterbrechende Änderung sein würde.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt zwei Methoden. Eine Methode verstößt gegen die Regel, und die andere Methode der Regel entspricht.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)
