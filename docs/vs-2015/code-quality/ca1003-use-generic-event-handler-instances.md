---
title: 'CA1003: generische Ereignishandlerinstanzen verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ee0571e85a1d4ec9960e0235814fcb9d7adbd483
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539905"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Generische Ereignishandlerinstanzen verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ enthält einen Delegaten, der "void" zurückgibt, dessen Signatur zwei Parameter enthält (das erste Objekt und das zweite einen Typ, der EventArgs zugewiesen werden kann) und die enthaltenden Assembly-Ziele [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Beschreibung der Regel
 Vor [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] musste ein neuer Delegat deklariert werden, der eine von der-Klasse abgeleitete Klasse angibt, um benutzerdefinierte Informationen an den-Ereignishandler zu übergeben <xref:System.EventArgs?displayProperty=fullName> . Dies ist in nicht mehr der Fall, in dem der Delegat [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] eingeführt wurde <xref:System.EventHandler%601?displayProperty=fullName> . Mit diesem generischen Delegaten kann jede Klasse, die von abgeleitet ist, <xref:System.EventArgs> in Verbindung mit dem-Ereignishandler verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den-Delegaten, und ersetzen Sie dessen Verwendung mithilfe des-Delegaten <xref:System.EventHandler%601?displayProperty=fullName> . Wenn der Delegat vom Compiler automatisch generiert wird [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , ändern Sie die Syntax der Ereignis Deklaration, um den Delegaten zu verwenden <xref:System.EventHandler%601?displayProperty=fullName> .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Delegaten, der gegen die Regel verstößt. In dem [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Beispiel wird beschrieben, wie das Beispiel geändert wird, um die Regel zu erfüllen. Im c#-Beispiel folgt ein Beispiel, das den geänderten Code anzeigt.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Delegatdeklaration aus dem vorherigen Beispiel entfernt, die die Regel erfüllt, und die Verwendung in den `ClassThatRaisesEvent` Methoden und ersetzt, indem der-Delegat `ClassThatHandlesEvent` verwendet wird <xref:System.EventHandler%601?displayProperty=fullName> .

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen.](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Nach Möglichkeit Generics verwenden.](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Weitere Informationen
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
