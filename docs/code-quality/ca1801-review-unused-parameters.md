---
title: "CA1801: Nicht verwendete Parameter überprüfen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1bb8c38d1436ca687664f92bfe0ba6db1ccf68ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Nicht verwendete Parameter überprüfen
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn das Element nicht außerhalb der Assembly, unabhängig von der Änderung angezeigt wird, die Sie vornehmen.<br /><br /> Nicht unterbrechend – Wenn Sie das Element den Parameter innerhalb des Textkörpers Verwendung ändern.<br /><br /> Unterbrechend – Wenn Sie den Parameter entfernen und außerhalb der Assembly sichtbar ist.|  
  
## <a name="cause"></a>Ursache  
 Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird. Mit dieser Regel wird nicht überprüfen Sie die folgenden Methoden:  
  
-   Methoden, die ein Delegat verweist.  
  
-   Methoden, die als Ereignishandler verwendet werden.  
  
-   Methoden deklariert werden, mit der `abstract` (`MustOverride` in Visual Basic) Modifizierer.  
  
-   Methoden deklariert werden, mit der `virtual` (`Overridable` in Visual Basic) Modifizierer.  
  
-   Methoden deklariert werden, mit der `override` (`Overrides` in Visual Basic) Modifizierer.  
  
-   Methoden deklariert werden, mit der `extern` (`Declare` -Anweisung in Visual Basic) Modifizierer.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Überprüfen Sie die Parameter in nicht virtuelle Methoden, die nicht im Methodentext verwendet werden, um sicherzustellen, dass keine Richtigkeit vorhanden ist, um den Zugriff darauf möglich. Nicht verwendete Parameter fallen Kosten für Wartung und Leistung.  
  
 Manchmal kann ein Verstoß gegen diese Regel zu einem Implementierungsfehler in der Methode hinweisen. Z. B. sollte der Parameter im Methodentext verwendet haben. Unterdrücken Sie Warnungen gegen diese Regel aus, wenn der Parameter hat aufgrund der Abwärtskompatibilität vorhanden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den nicht verwendeten Parameter (eine unterbrechende Änderung), oder verwenden Sie den Parameter im Methodentext (eine nicht unterbrechende Änderung).  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel für zuvor gelieferten Code, für den die Lösung eine unterbrechende Änderung wäre.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt zwei Methoden. Eine Methode verstößt gegen die Regel, und die andere Methode erfüllt, die die Regel.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)