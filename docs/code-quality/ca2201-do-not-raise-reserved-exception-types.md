---
title: 'CA2201: Keine reservierten Ausnahmetypen auslösen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d9b787a4e50f43867b5d9b4ec7a11aba03f8599
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231673"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Keine reservierten Ausnahmetypen auslösen.

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methode löst einen Ausnahmetyp aus, der zu allgemein ist oder von der Laufzeit reserviert ist.

## <a name="rule-description"></a>Regelbeschreibung

Die folgenden Ausnahme Typen sind zu allgemein, um dem Benutzer ausreichende Informationen bereitzustellen:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

Die folgenden Ausnahme Typen sind reserviert und sollten nur vom Common Language Runtime ausgelöst werden:

- <xref:System.AccessViolationException?displayProperty=fullName>

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.ExternalException?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SEHException?displayProperty=fullName>

- <xref:System.StackOverflowException?displayProperty=fullName>

**Keine allgemeinen Ausnahmen auslösen**

Wenn Sie einen allgemeinen Ausnahmetyp auslösen, z <xref:System.Exception> . <xref:System.SystemException> b. oder in einer Bibliothek oder einem Framework, erzwingen Sie, dass Consumer alle Ausnahmen abfangen, einschließlich unbekannter Ausnahmen, die nicht behandelt werden müssen.

Stattdessen lösen Sie entweder einen stärker abgeleiteten Typ aus, der bereits im Framework vorhanden ist, oder erstellen Sie einen eigenen <xref:System.Exception>Typ, der von abgeleitet wird.

**Auslösen spezifischer Ausnahmen**

Die folgende Tabelle zeigt Parameter und die Ausnahmen, die bei der Validierung des Parameters ausgelöst werden müssen, einschließlich des value-Parameters im Set-Accessor einer Eigenschaft:

|Parameter Beschreibung|Ausnahme|
|---------------------------|---------------|
|`null`Angabe|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Außerhalb des zulässigen Wertebereichs (z. b. ein Index für eine Sammlung oder Liste)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Ungültiger `enum` Wert|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Enthält ein Format, das den Parameter Spezifikationen einer Methode (z. b. der Format Zeichenfolge `ToString(String)`für) nicht entspricht.|<xref:System.FormatException?displayProperty=fullName>|
|Andernfalls ungültig|<xref:System.ArgumentException?displayProperty=fullName>|

Wenn ein Vorgang für den aktuellen Zustand eines Objekt auslösenden ungültig ist<xref:System.InvalidOperationException?displayProperty=fullName>

Wenn ein Vorgang für ein Objekt durchgeführt wird, das verworfen wurde.<xref:System.ObjectDisposedException?displayProperty=fullName>

Wenn ein Vorgang nicht unterstützt wird (z. b. in einem überschriebenen **Stream. Schreiben** in einem zum Lesen geöffneten Stream) throw<xref:System.NotSupportedException?displayProperty=fullName>

Wenn eine Konvertierung zu einem Überlauf führen würde (z. b. in einer expliziten Cast Operator Überladung), Throw<xref:System.OverflowException?displayProperty=fullName>

In allen anderen Situationen sollten Sie einen eigenen Typ erstellen, der von <xref:System.Exception> abgeleitet ist, und diesen auslösen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ der ausgelösten Ausnahme in einen bestimmten Typ, bei dem es sich nicht um einen der reservierten Typen handelt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1031: Allgemeine Ausnahme Typen nicht auffangen](../code-quality/ca1031-do-not-catch-general-exception-types.md)
