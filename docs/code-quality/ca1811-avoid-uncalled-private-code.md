---
title: 'CA1811: Nicht aufgerufenen privaten Code vermeiden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fc7bac9804c42cb7910df6b6d89ad766b09ee0d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Nicht aufgerufenen privaten Code vermeiden
|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|Kategorie|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein privater oder internen (auf Assemblyebene)-Member in der Assembly keine Aufrufer, wird nicht aufgerufen werden, indem die common Language Runtime und nicht durch einen Delegaten aufgerufen. Die folgenden Member werden nicht durch diese Regel überprüft:  
  
-   Explizite Mitglieder.  
  
-   Statische Konstruktoren.  
  
-   Serialisierungskonstruktoren.  
  
-   Mit markierte Methoden <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
-   Elemente, die Außerkraftsetzungen beschränkt sind.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Mit dieser Regel kann Berichts falsch positive Ergebnisse, wenn Einstiegspunkte Auftreten von der Regellogik derzeit nicht identifiziert werden. Darüber hinaus kann ein Compiler nicht aufrufbaren Code in eine Assembly ausgeben.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den aufrufbaren Code aus, oder fügen Sie Code, den sie aufruft.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)