---
title: 'CA1024: Nach Möglichkeit Eigenschaften verwenden.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2763d7dd167ad0027509c44b8f9d43523f03976b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547797"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Nach Möglichkeit Eigenschaften verwenden.

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methode hat einen Namen, der mit `Get`beginnt, keine Parameter annimmt und einen Wert zurückgibt, der kein Array ist.

Standardmäßig untersucht diese Regel nur öffentliche und geschützte Methoden, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

In den meisten Fällen stellen Eigenschaften Daten dar, und Methoden führen Aktionen aus. Auf Eigenschaften wird wie Felder zugegriffen, sodass Sie einfacher zu verwenden sind. Eine Methode ist ein guter Kandidat, wenn eine der folgenden Bedingungen vorliegt:

- Nimmt keine Argumente an und gibt die Zustandsinformationen eines Objekts zurück.

- Akzeptiert ein einzelnes Argument, um einen Teil des Zustands eines Objekts festzulegen.

Eigenschaften sollten sich so Verhalten, als handele es sich um Felder. Wenn die Methode dies nicht möglich ist, sollte Sie nicht in eine Eigenschaft geändert werden. Methoden sind in den folgenden Situationen besser als Eigenschaften:

- Die-Methode führt einen zeitaufwändigen Vorgang aus. Die-Methode ist möglicherweise langsamer als die Zeit, die erforderlich ist, um den Wert eines Felds festzulegen oder zu erhalten.

- Die Methode führt eine Konvertierung aus. Beim Zugriff auf ein Feld wird keine konvertierte Version der Daten zurückgegeben, die gespeichert wird.

- Die Get-Methode hat einen beobachtbaren Nebeneffekt. Das Abrufen des Werts eines Felds führt nicht zu Nebeneffekten.

- Die Ausführungsreihenfolge ist wichtig. Das Festlegen des Werts eines Felds beruht nicht auf dem Vorkommen anderer Vorgänge.

- Wenn Sie die Methode zweimal nacheinander aufrufen, werden andere Ergebnisse erzeugt.

- Die Methode ist statisch, gibt jedoch ein Objekt zurück, das vom Aufrufer geändert werden kann. Das Abrufen des Werts eines Felds ermöglicht dem Aufrufer nicht, die Daten zu ändern, die vom Feld gespeichert werden.

- Die-Methode gibt ein Array zurück.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die-Methode in eine-Eigenschaft.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrückt eine Warnung aus dieser Regel, wenn die Methode mindestens eines der zuvor aufgelisteten Kriterien erfüllt.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1024.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="control-property-expansion-in-the-debugger"></a>Steuern der Eigenschafts Erweiterung im Debugger

Ein Grund, warum Programmierer die Verwendung einer Eigenschaft vermeiden, liegt darin, dass Sie vom Debugger nicht automatisch erweitert werden sollen. Die-Eigenschaft kann z. b. das Zuordnen eines großen Objekts oder das Aufrufen eines P/Call-Objekts einschließen, aber es sind möglicherweise tatsächlich keine Nebeneffekte vorhanden.

Sie können verhindern, dass der Debugger die Eigenschaften durch Anwenden <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>von automatisch erweitert. Das folgende Beispiel zeigt, wie dieses Attribut auf eine Instanzeigenschaft angewendet wird.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp
using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]
            }
        }
    }
}
```

## <a name="example"></a>Beispiel

Das folgende Beispiel enthält mehrere Methoden, die in Eigenschaften konvertiert werden sollten, und mehrere Methoden, die nicht, weil Sie sich nicht wie Felder Verhalten.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]