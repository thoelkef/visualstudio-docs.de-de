---
title: 'CA2201: Keine reservierten Ausnahmetypen auslösen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: be0fc7df23e7164371e95e92fbad1a32026284df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227067"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Keine reservierten Ausnahmetypen auslösen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode löst einen Ausnahmetyp, die zu allgemein oder von der Laufzeit reserviert ist.

## <a name="rule-description"></a>Regelbeschreibung
 Die folgenden Ausnahmetypen sind zu Allgemein, genügend Informationen für Benutzer bereit:

-   <xref:System.Exception?displayProperty=fullName>

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.SystemException?displayProperty=fullName>

 Die folgenden Ausnahmetypen sind reserviert und darf nur durch die common Language Runtime ausgelöst werden:

-   <xref:System.ExecutionEngineException?displayProperty=fullName>

-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>

-   <xref:System.NullReferenceException?displayProperty=fullName>

-   <xref:System.OutOfMemoryException?displayProperty=fullName>

 **Lösen Sie keine allgemeine Ausnahmen**

 Wenn Sie einen Typ allgemeine Ausnahme, z. B. auslösen <xref:System.Exception> oder <xref:System.SystemException> in einer Bibliothek oder einem Framework, erzwingt diese Consumer zum Abfangen aller Ausnahmen, einschließlich Unbekannte Ausnahmen, die sie nicht wissen, wie behandelt.

 Stattdessen entweder auslösen ein stärker abgeleiteten Typs, die im Framework bereits vorhanden ist, oder erstellen Sie Ihre eigenen von abgeleiteter Typ <xref:System.Exception>.

 **Bestimmte Ausnahmen auslösen**

 Die folgende Tabelle zeigt die Parameter und welche Ausnahmen auslöst, wenn Sie überprüfen, den Parameter ob, einschließlich des Value-Parameters in der Set-Accessor einer Eigenschaft:

|Parameterbeschreibung|Ausnahme|
|---------------------------|---------------|
|`null` Referenz|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Außerhalb des zulässigen Bereichs von Werten (z. B. ein Index für eine Sammlung oder Liste)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Ungültige `enum` Wert|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Enthält ein Format, das nicht die Parameterspezifikationen der eine Methode erfüllt (z. B. die Formatzeichenfolge für `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|
|Ungültig ist|<xref:System.ArgumentException?displayProperty=fullName>|

 Wenn ein Vorgang für den aktuellen Status ausgelöst ist ungültig <xref:System.InvalidOperationException?displayProperty=fullName>

 Wenn ein Vorgang für ein Objekt ausgeführt wird, das verworfen wurde ausgelöst <xref:System.ObjectDisposedException?displayProperty=fullName>

 Wenn ein Vorgang wird nicht unterstützt (z. B. eine überschriebene **Stream.Write** in einen Stream zum Lesen geöffnet) auslösen <xref:System.NotSupportedException?displayProperty=fullName>

 Wenn eine Konvertierung zu einem Überlauf (z. B. in eine explizite Umwandlung operatorüberladung) führen würde auslösen <xref:System.OverflowException?displayProperty=fullName>

 Für alle anderen Fälle empfiehlt sich, Ihre eigenen von abgeleiteter Typ <xref:System.Exception> und auszulösen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ der ausgelösten Ausnahme für einen bestimmten Typ, der nicht zu den reservierten Typen ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1031: Allgemeine Ausnahmetypen nicht auffangen](../code-quality/ca1031-do-not-catch-general-exception-types.md)



