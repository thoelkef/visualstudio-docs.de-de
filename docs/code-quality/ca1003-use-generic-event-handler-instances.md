---
title: 'CA1003: Generische Ereignishandlerinstanzen verwenden.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: eff7b4b880526909c293e16aa32ae7045bcdf297
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62780033"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Generische Ereignishandlerinstanzen verwenden.

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ enthält einen Delegaten, die "void" zurückgibt und die Signatur enthält zwei Parameter (der erste ist ein Objekt und das zweite ein Typ, der EventArgs zugewiesen werden) und der enthaltenden Assembly Ziele.

Diese Regel nur sucht standardmäßig an extern sichtbare Typen, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Vor, um benutzerdefinierte Informationen an den Ereignishandler übergeben ein neuer Delegat musste deklariert werden, die eine Klasse, die von abgeleitet wurde angegeben, die <xref:System.EventArgs?displayProperty=fullName> Klasse. Dies gilt nicht mehr in .NET. .NET Framework eingeführt, die <xref:System.EventHandler%601?displayProperty=fullName> Delegat, der einen generischen Delegaten, die jede Klasse ermöglicht, das von abgeleitet ist <xref:System.EventArgs> , zusammen mit der Ereignishandler verwendet werden soll.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Delegaten, und Ersetzen Sie die Verwendung durch die <xref:System.EventHandler%601?displayProperty=fullName> delegieren.

Wenn der Delegat automatisch von Visual Basic-Compiler ist, ändern Sie die Syntax der Deklaration des Ereignisses mit der <xref:System.EventHandler%601?displayProperty=fullName> delegieren.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1003.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein Delegat, der gegen die Regel verstößt. In der Visual Basic-Beispiel beschrieben Kommentare, wie ändern Sie das Beispiel, um die Regel erfüllen. Für das C#-Beispiel folgt ein Beispiel, das den geänderten Code zeigt.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

Der folgende Codeausschnitt entfernt der Delegatdeklaration überein, aus dem vorherigen Beispiel, das in der Regel entspricht. Er ersetzt die Verwendung in der `ClassThatRaisesEvent` und `ClassThatHandlesEvent` Methoden mithilfe der <xref:System.EventHandler%601?displayProperty=fullName> delegieren.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: Statische Member in generischen Typen nicht deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: Verwenden Sie Generika](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch

- [Generika](/dotnet/csharp/programming-guide/generics/index)