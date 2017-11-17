---
title: ': CA1700 nicht Enumerationswerte &#39; Reservierte &#39; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2acfafaec213f619dbe8c3077ab5cc72bdfde88d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>: CA1700 nicht Enumerationswerte &#39; Reservierte &#39;
|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Der Name der Enumerationsmember enthält das Wort "reserved".  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen. Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung. Sie sollte nicht erwarten, dass Benutzer, um ein Element zu ignorieren, nur weil der Name "reserved" enthält, noch können Sie sich auf Benutzer zu lesen oder Dokumentation Abbrüchen verlassen. Darüber hinaus da reservierten Member im Objektbrowser und intelligenten integrierten entwicklungsumgebungen angezeigt werden, können sie zu Verwirrung führen dazu, welche Elemente tatsächlich verwendet werden.  
  
 Anstatt ein reserviertes Element zu verwenden, fügen Sie der Enumeration in einer zukünftigen Version ein neues Element hinzu. In den meisten Fällen ist das Hinzufügen des neuen Mitglieds keine unterbrechende Änderung, solange die Hinzufügung nicht die Werte von der ursprünglichen Elemente ändern kann.  
  
 In einer begrenzten Anzahl von Fällen ist das Hinzufügen eines Elements eine unterbrechende Änderung, auch wenn die ursprünglichen Elemente auf ihre ursprünglichen Werte beibehalten. Das neue Element kann nicht in erster Linie von vorhandenen Codepfaden zurückgegeben werden, ohne Unterbrechung Aufrufer, mit denen eine `switch` (`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Anweisung für den Rückgabewert, umfasst die gesamte Memberliste und, die eine Ausnahme in, der der Standardfall. Eine sekundäre Rolle spielt, dass Clientcode wie z. B. keine Änderungen im Verhalten von Reflektionsmethoden verarbeiten kann <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. Dementsprechend ist, wenn das neue Element wurde aus der vorhandenen Methoden zurückgegeben werden, oder eine bekannte Anwendungsinkompatibilität aufgrund schlechter tritt auf, die einzige geschützte Lösung an:  
  
1.  Fügen Sie eine neue Enumeration, die die ursprünglichen und die neuen Elemente enthält.  
  
2.  Markieren Sie die ursprüngliche Enumeration mit den <xref:System.ObsoleteAttribute?displayProperty=fullName> Attribut.  
  
 Führen Sie dieses Verfahren für extern sichtbare Typen oder Member, die die ursprüngliche Enumeration verfügbar machen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie oder benennen Sie den Member.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel für ein Element, das derzeit verwendet wird oder Bibliotheken, die zuvor versendet habe.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: Der Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)