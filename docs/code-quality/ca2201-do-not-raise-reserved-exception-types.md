---
title: "CA2201: Keine reservierten Ausnahmetypen ausl&#246;sen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotRaiseReservedExceptionTypes"
  - "CA2201"
helpviewer_keywords: 
  - "CA2201"
  - "DoNotRaiseReservedExceptionTypes"
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2201: Keine reservierten Ausnahmetypen ausl&#246;sen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methode löst einen Ausnahmetyp aus, der zu allgemein oder von der Laufzeit reserviert ist.  
  
## Regelbeschreibung  
 Die folgenden Ausnahmetypen sind zu allgemein, um dem Benutzer ausreichend Informationen bereitzustellen:  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 Die folgenden Ausnahmetypen sind reserviert und sollten nur von der Common Language Runtime ausgelöst werden:  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **Keine allgemeinen Ausnahmen auslösen**  
  
 Wenn Sie einen allgemeinen Ausnahmetyp wie <xref:System.Exception> oder <xref:System.SystemException> in einer Bibliothek oder einem Framework auslösen, werden Consumer gezwungen, alle Ausnahmen abzufangen, einschließlich unbekannter Ausnahmen, die sie nicht behandeln können.  
  
 Lösen Sie entweder einen stärker abgeleiteten Typ aus, der bereits im Framework vorhanden ist, oder erstellen Sie einen eigenen Typ, der von <xref:System.Exception> abgeleitet wird.  
  
 **Bestimmte Ausnahmen auslösen**  
  
 In der folgenden Tabelle sind die Parameter und Ausnahmen enthalten, die beim Validieren des Parameters ausgelöst werden, einschließlich des Wertparameters im set\-Accessor einer Eigenschaft:  
  
|Parameterbeschreibung|Ausnahme|  
|---------------------------|--------------|  
|`null`\-Referenz|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Außerhalb des zulässigen Wertebereichs \(z. B. ein Index für eine Auflistung oder eine Liste\)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Ungültiger `enum`\-Wert|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Enthält ein Format, das die Parameterangaben einer Methode nicht erfüllt \(z. B. die Formatzeichenfolge für `ToString(String)`\).|<xref:System.FormatException?displayProperty=fullName>|  
|Andernfalls ungültig|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Wenn eine Operation ungültig für den aktuellen Objektzustand ist, wird <xref:System.InvalidOperationException?displayProperty=fullName> ausgelöst.  
  
 Wenn eine Operation für ein verworfenes Objekt ausgeführt wird, wird <xref:System.ObjectDisposedException?displayProperty=fullName> ausgelöst.  
  
 Wenn eine Operation nicht unterstützt wird \(wie in einem überschriebenen **Stream.Write** in einem zum Lesen geöffneten Stream\), wird <xref:System.NotSupportedException?displayProperty=fullName> ausgelöst.  
  
 Wenn eine Konvertierung zu einem Überlauf führt \(wie in einer expliziten Umwandlungsoperatorüberladung\), wird <xref:System.OverflowException?displayProperty=fullName> ausgelöst.  
  
 In allen anderen Situationen sollten Sie erwägen, Ihren eigenen Typ zu erstellen, der von <xref:System.Exception> abgeleitet wird, und diesen auslösen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ der Ausnahme, die ausgelöst wird, in einen speziellen Typ, der kein reservierter Typ ist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Verwandte Regeln  
 [CA1031: Allgemeine Ausnahmetypen nicht auffangen](../code-quality/ca1031-do-not-catch-general-exception-types.md)