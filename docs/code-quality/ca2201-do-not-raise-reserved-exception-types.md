---
title: "CA2201: Keine reservierten Ausnahmetypen auslösen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 713018b96aed70d52b1b11e75b0c2993312ef474
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: Keine reservierten Ausnahmetypen auslösen
|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine Methode löst einen Ausnahmetyp, ist zu allgemein oder von der Laufzeit reserviert ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die folgenden Ausnahmetypen sind zu Allgemein, über ausreichende Anmeldeinformationen für den Benutzer:  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 Die folgenden Ausnahmetypen sind reserviert und sollte nur von der common Language Runtime ausgelöst werden:  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **Lösen Sie nicht allgemeine Ausnahmen**  
  
 Wenn Sie einen Typ allgemeine Ausnahme, z. B. auslösen <xref:System.Exception> oder <xref:System.SystemException> in einer Bibliothek oder einem Framework, erzwingt es Consumern, alle catch Ausnahmen, einschließlich Unbekannte Ausnahmen, die sie nicht wissen, wie behandeln.  
  
 Stattdessen entweder auslösen ein stärker abgeleiteten Typs, der bereits im Framework vorhanden ist, oder erstellen Sie einen eigene aus abgeleiteter Typ <xref:System.Exception>.  
  
 **Bestimmte Ausnahmen auslösen**  
  
 In der folgenden Tabelle werden die Parameter aufgeführt, und welche Ausnahmen auslösen, wenn den Parameter, einschließlich der Value-Parameter in der Set-Accessor einer Eigenschaft zu überprüfen:  
  
|Beschreibung des Parameters|Ausnahme|  
|---------------------------|---------------|  
|`null`Referenz|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Außerhalb des zulässigen Bereichs von Werten (z. B. einen Index für eine Auflistung oder Liste)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Ungültige `enum` Wert|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Enthält ein Format, das nicht den Parameterspezifikationen einer Methode entspricht (z. B. die Formatzeichenfolge für `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|  
|Andernfalls ungültig|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Wenn ein Vorgang für den aktuellen Status ausgelöst ungültige ist.<xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Wenn ein Vorgang für ein Objekt ausgeführt wird, das verworfen wurde ausgelöst<xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Wenn ein Vorgang wird nicht unterstützt (z. B. in eine überschriebene **Stream.Write** in einen Stream, der zum Lesen geöffnet) auslösen<xref:System.NotSupportedException?displayProperty=fullName>  
  
 Wenn eine Konvertierung zu einem Überlauf (z. B. in eine explizite Umwandlung operatorüberladung) bedingt auslösen<xref:System.OverflowException?displayProperty=fullName>  
  
 Für alle anderen Situationen Estellen Sie einen eigene aus abgeleiteter Typ <xref:System.Exception> und diesen auslösen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ der ausgelösten Ausnahme für einen bestimmten Typ, der nicht zu den reservierten Typen ist.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1031: Allgemeine Ausnahmetypen nicht auffangen](../code-quality/ca1031-do-not-catch-general-exception-types.md)