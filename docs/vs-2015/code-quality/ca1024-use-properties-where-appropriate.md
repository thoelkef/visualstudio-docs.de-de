---
title: 'CA1024: Eigenschaften nach Bedarf verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a240a6eea86075bbf7f721f8620b6d135d594c20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546665"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Nach Möglichkeit Eigenschaften verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode hat einen Namen, der mit beginnt `Get` , keine Parameter annimmt und einen Wert zurückgibt, der kein Array ist.

## <a name="rule-description"></a>Beschreibung der Regel
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

## <a name="controlling-property-expansion-in-the-debugger"></a>Steuern der Eigenschafts Erweiterung im Debugger
 Ein Grund, warum Programmierer die Verwendung einer Eigenschaft vermeiden, besteht darin, dass Sie vom Debugger nicht automatisch erweitert werden sollen. Die-Eigenschaft kann z. b. das Zuordnen eines großen Objekts oder das Aufrufen eines P/Call-Objekts einschließen, aber es sind möglicherweise tatsächlich keine Nebeneffekte vorhanden.

 Sie können verhindern, dass der Debugger die Eigenschaften automatisch erweitert, indem Sie anwenden <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName> . Das folgende Beispiel zeigt, wie dieses Attribut auf eine Instanzeigenschaft angewendet wird.

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
```

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält mehrere Methoden, die in Eigenschaften konvertiert werden sollten, und einige, die nicht, weil Sie sich nicht wie Felder Verhalten.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
