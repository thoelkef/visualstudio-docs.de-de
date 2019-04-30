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
ms.openlocfilehash: e4008872a7cb96386ef702d21ba8a18d96037d83
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779382"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Nach Möglichkeit Eigenschaften verwenden.

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methode hat einen Namen, die mit beginnt `Get`nimmt keine Parameter und gibt einen Wert, der kein Array ist.

Diese Regel nur sucht standardmäßig an öffentliche und geschützte Methoden, dies ist jedoch [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Klicken Sie in den meisten Fällen Eigenschaften Daten darstellen, und Methoden Aktionen ausführen. Eigenschaften sind zugegriffen, wie Felder, wodurch sie einfacher zu verwenden. Eine Methode ist, eignet sich für eine Eigenschaft zu werden, wenn eine der folgenden Bedingungen vorliegt:

- Akzeptiert keine Argumente und gibt Informationen über den Zustand eines Objekts.

- Akzeptiert ein einzelnes Argument um einen Teil des Zustands eines Objekts festzulegen.

Eigenschaften sollten Verhalten, als wären sie Felder. Wenn die Methode nicht möglich ist, sollten sie nicht auf eine Eigenschaft geändert werden. Methoden sind besser als Eigenschaften in den folgenden Situationen:

- Die Methode ausführt einen zeitaufwändigen Vorgang. Die Methode ist als die Zeit, die erforderlich sind, um festzulegen, oder rufen Sie den Wert eines Felds beansprucht.

- Die Methode führt eine Konvertierung aus. Zugreifen auf ein Feld gibt keine konvertierte Version der Daten zurück, die sie speichert.

- Die Get-Methode hat es sich um ein Observable Nebeneffekt. Abrufen des Werts eines Felds ergibt keinen keine Nebeneffekte.

- Die Reihenfolge der Ausführung ist wichtig. Festlegen des Werts eines Felds beruht nicht auf das Vorhandensein anderer Vorgänge.

- Aufrufen der Methode zweimal hintereinander führt zu unterschiedlichen Ergebnissen.

- Die Methode ist statisch, aber es gibt ein Objekt, das vom Aufrufer geändert werden kann. Abrufen des Werts eines Felds lässt nicht den Aufrufer so ändern Sie die Daten, die nach dem Feld gespeichert wird.

- Die Methode gibt ein Array zurück.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Methode einer Eigenschaft ein.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel, wenn die Methode, die mindestens eines der zuvor aufgeführten Kriterien erfüllt.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1024.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="control-property-expansion-in-the-debugger"></a>Steuerelement-Eigenschaft-Erweiterung im debugger

Ein Grund, die Programmierer verwenden Sie eine Eigenschaft ist, da sie nicht möchten, dass der Debugger automatisch, dass es. Beispielsweise die Eigenschaft wird eventuell ein großes Objekt zuweisen oder P/Invoke aufrufen, aber es möglicherweise nicht tatsächlich keine Observable Nebeneffekte.

Sie können den Debugger von Autoexpanding Eigenschaften verhindern, durch Anwenden von <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. Das folgende Beispiel zeigt dieses Attribut auf eine Instance-Eigenschaft angewendet wird.

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

Das folgende Beispiel enthält mehrere Methoden, Eigenschaften konvertiert werden sollen, und mehrere Funktionen, sollte nicht verwendet werden, da sie sich wie Felder Verhalten nicht.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]