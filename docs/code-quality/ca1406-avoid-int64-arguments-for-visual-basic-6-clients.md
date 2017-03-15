---
title: "CA1406: Int64-Argumente f&#252;r Visual Basic 6-Clients vermeiden | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
helpviewer_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1406: Int64-Argumente f&#252;r Visual Basic 6-Clients vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ, der ausdrücklich als für COM \(Component Object Model\) sichtbar markiert ist, deklariert einen Member, der ein <xref:System.Int64?displayProperty=fullName>\-Argument akzeptiert.  
  
## Regelbeschreibung  
 Visual Basic 6\-COM\-Clients können nicht auf 64\-Bit\-Ganzzahlen zugreifen.  
  
 Standardmäßig sind folgende Programmierelemente für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member öffentlicher Werttypen.  Um jedoch die Anzahl falscher positiver Ergebnisse zu verringern, muss entsprechend der Regel die COM\-Sichtbarkeit des Typs explizit angegeben werden, die enthaltende Assembly muss mit dem auf `false` festgelegten <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>\-Attribut markiert sein, und der Typ muss mit dem auf `true` festgelegten <xref:System.Runtime.InteropServices.ComVisibleAttribute>\-Attribut markiert sein.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel für einen Parameter, dessen Wert immer als 32\-Bit\-Ganzzahl ausgedrückt werden kann, zu beheben, ändern Sie den Parametertyp in <xref:System.Int32?displayProperty=fullName>.  Wenn der Wert des Parameters größer sein darf, als mit einer 32\-Bit\-Ganzzahl ausgedrückt werden kann, ändern Sie den Parametertyp in <xref:System.Decimal?displayProperty=fullName>.  Beachten Sie, dass sowohl <xref:System.Single?displayProperty=fullName> als auch <xref:System.Double?displayProperty=fullName> in den oberen Bereichen des <xref:System.Int64>\-Datentyps an Genauigkeit verlieren.  Wenn ein Member nicht für COM sichtbar sein soll, markieren Sie diesen mit dem auf `false` festgelegten <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn sichergestellt ist, dass keine Visual Basic 6\-COM\-Clients auf den Typ zugreifen.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  
  
 [!code-cs[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## Verwandte Regeln  
 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Siehe auch  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)