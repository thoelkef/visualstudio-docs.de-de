---
title: 'CA2134: Methoden müssen beim Überschreiben von Basis Methoden eine konsistente Transparenz bewahren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96910ffc53e6c48f930232c83d87570f1bc71e00
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608923"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Methodsmustoverride withkonsistenttransparenz|
|CheckId|CA2134|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Diese Regel wird ausgelöst, wenn eine mit dem <xref:System.Security.SecurityCriticalAttribute> markierte Methode eine Methode überschreibt, die transparent oder mit der <xref:System.Security.SecuritySafeCriticalAttribute> markiert ist. Die Regel wird auch ausgelöst, wenn eine Methode, die transparent oder mit dem <xref:System.Security.SecuritySafeCriticalAttribute> markiert ist, eine mit einer <xref:System.Security.SecurityCriticalAttribute> markierte Methode überschreibt.

 Die Regel wird angewendet, wenn eine virtuelle Methode überschrieben oder eine Schnittstelle implementiert wird.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird für Versuche ausgelöst, den Sicherheits Zugriff einer Methode weiter oben in der Vererbungs Kette zu ändern. Wenn eine virtuelle Methode in einer Basisklasse z. b. transparent oder sicherheitsrelevant ist, muss Sie von der abgeleiteten Klasse mit einer transparenten oder sicherheitskritischen Methode überschrieben werden. Umgekehrt muss die abgeleitete Klasse diese mit einer sicherheitskritischen Methode überschreiben, wenn Sie sicherheitskritisch ist. Die gleiche Regel gilt für die Implementierung von Schnittstellen Methoden.

 Transparenzregeln werden erzwungen, wenn der Code anstelle der Laufzeit JIT kompiliert wird, sodass die Transparenz Berechnung nicht über dynamische Typinformationen verfügt. Daher muss das Ergebnis der Transparenz Berechnung in der Lage sein, nur von den statischen Typen zu bestimmen, die JIT-kompiliert werden, unabhängig vom dynamischen Typ.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Transparenz der Methode, die eine virtuelle Methode überschreibt, oder implementieren Sie eine Schnittstelle, die der Transparenz der virtuellen oder Schnittstellen Methode entspricht.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Warnungen von dieser Regel nicht unterdrücken. Verstöße gegen diese Regel führen zu einer Laufzeit <xref:System.TypeLoadException> für Assemblys, die Transparenz der Ebene 2 verwenden.

## <a name="examples"></a>Beispiele

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Siehe auch
 [Sicherheits transparenter Code, Ebene 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
