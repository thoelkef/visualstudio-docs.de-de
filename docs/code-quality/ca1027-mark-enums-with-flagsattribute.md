---
title: "CA1027: Enumerationen mit FlagsAttribute markieren | Microsoft Docs"
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
  - "MarkEnumsWithFlags"
  - "CA1027"
helpviewer_keywords: 
  - "CA1027"
  - "MarkEnumsWithFlags"
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1027: Enumerationen mit FlagsAttribute markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Die Werte einer öffentlichen Enumeration sind Potenzen von 2 oder Kombinationen anderer in der Enumeration definierter Werte. Das <xref:System.FlagsAttribute?displayProperty=fullName>\-Attribut ist nicht vorhanden.  Damit weniger falsche Positiva produziert werden, meldet diese Regel keinen Verstoß bei Enumerationen mit fortlaufenden Werten.  
  
## Regelbeschreibung  
 Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert.  Wenden Sie <xref:System.FlagsAttribute> auf eine Enumeration an, wenn deren benannte Konstanten sinnvoll kombiniert werden können.  Betrachten Sie z. B. eine Enumeration der Wochentage in einer Anwendung, die erfasst, welche Tagesressourcen verfügbar sind.  Wenn die Verfügbarkeit jeder Ressource mithilfe der Enumeration codiert wird, die <xref:System.FlagsAttribute> besitzt, kann eine beliebige Kombination von Tagen dargestellt werden.  Ohne das Attribut kann nur 1 Tag der Woche dargestellt werden.  
  
 Bei Feldern, in denen kombinierbare Enumerationen gespeichert werden, werden die einzelnen Enumerationswerte im Feld als Bitgruppen behandelt.  Daher werden solche Felder gelegentlich als *Bitfelder* bezeichnet.  Um Enumerationswerte für die Speicherung in einem Bitfeld zu kombinieren, verwenden Sie die booleschen Bedingungsoperatoren.  Wenn Sie ein Bitfeld auf das Vorhandensein eines bestimmten Enumerationswerts testen möchten, verwenden Sie die booleschen logischen Operatoren.  Damit ein Bitfeld kombinierte Enumerationswerte richtig speichert und abruft, muss jeder in der Enumeration definierte Wert eine Potenz von 2 sein.  Nur in diesem Fall können die booleschen logischen Operatoren die im Feld gespeicherten einzelnen Enumerationswerte extrahieren.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Enumeration <xref:System.FlagsAttribute> hinzu.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn die Enumerationswerte nicht kombinierbar sein sollen.  
  
## Beispiel  
 Im folgenden Beispiel ist `DaysEnumNeedsFlags` eine Enumeration, die den Anforderungen an die Verwendung von <xref:System.FlagsAttribute> entspricht, dieses Element jedoch nicht enthält.  Die `ColorEnumShouldNotHaveFlag`\-Enumeration verfügt nicht über Werte, die Potenzen von 2 sind, gibt <xref:System.FlagsAttribute> jedoch in fehlerhafter Weise an.  Dies verstößt gegen die Regel [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).  
  
 [!code-cs[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]  
  
## Verwandte Regeln  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Siehe auch  
 <xref:System.FlagsAttribute?displayProperty=fullName>