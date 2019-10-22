---
title: 'CA2201: keine reservierten Ausnahme Typen Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a550226a5ea1edb3b30e317be6b5682f4c204d52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667377"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Keine reservierten Ausnahmetypen auslösen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode löst einen Ausnahmetyp aus, der zu allgemein ist oder von der Laufzeit reserviert ist.

## <a name="rule-description"></a>Regelbeschreibung
 Die folgenden Ausnahme Typen sind zu allgemein, um dem Benutzer ausreichende Informationen bereitzustellen:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  Die folgenden Ausnahme Typen sind reserviert und sollten nur vom Common Language Runtime ausgelöst werden:

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **Keine allgemeinen Ausnahmen auslösen**

  Wenn Sie einen allgemeinen Ausnahmetyp auslösen, z. b. <xref:System.Exception> oder <xref:System.SystemException> in einer Bibliothek oder einem Framework, erzwingen Sie, dass Consumer alle Ausnahmen abfangen, einschließlich unbekannter Ausnahmen, die nicht behandelt werden können.

  Stattdessen lösen Sie entweder einen stärker abgeleiteten Typ aus, der bereits im Framework vorhanden ist, oder erstellen Sie einen eigenen Typ, der von <xref:System.Exception> abgeleitet ist.

  **Auslösen spezifischer Ausnahmen**

  Die folgende Tabelle zeigt Parameter und die Ausnahmen, die bei der Validierung des Parameters ausgelöst werden müssen, einschließlich des value-Parameters im Set-Accessor einer Eigenschaft:

|Parameter Beschreibung|-Ausnahme|
|---------------------------|---------------|
|`null`-Verweis|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Außerhalb des zulässigen Wertebereichs (z. b. ein Index für eine Sammlung oder Liste)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Ungültiger `enum`-Wert|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Enthält ein Format, das nicht den Parameter Spezifikationen einer Methode entspricht (z. b. die Format Zeichenfolge für `ToString(String)`).|<xref:System.FormatException?displayProperty=fullName>|
|Andernfalls ungültig|<xref:System.ArgumentException?displayProperty=fullName>|

 Wenn ein Vorgang für den aktuellen Zustand eines Objekts ungültig ist <xref:System.InvalidOperationException?displayProperty=fullName>

 Wenn ein Vorgang für ein Objekt ausgeführt wird, das verworfen wurde <xref:System.ObjectDisposedException?displayProperty=fullName>

 Wenn ein Vorgang nicht unterstützt wird (z. b. in einem überschriebenen **Stream. Schreiben** Sie in einen zum Lesen geöffneten Stream), lösen Sie <xref:System.NotSupportedException?displayProperty=fullName> aus.

 Wenn eine Konvertierung zu einem Überlauf führen würde (z. b. in einer expliziten Umwandlungs Operator Überladung), Throw <xref:System.OverflowException?displayProperty=fullName>

 In allen anderen Situationen sollten Sie einen eigenen Typ erstellen, der von <xref:System.Exception> abgeleitet ist, und dies auslösen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ der ausgelösten Ausnahme in einen bestimmten Typ, bei dem es sich nicht um einen der reservierten Typen handelt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1031: Allgemeine Ausnahmetypen nicht auffangen](../code-quality/ca1031-do-not-catch-general-exception-types.md)
