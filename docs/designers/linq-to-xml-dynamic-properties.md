---
title: "Dynamische Eigenschaften in LINQ to XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Dynamische Eigenschaften in LINQ to XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Abschnitt enthält Referenzinformationen zu den dynamischen Eigenschaften in LINQ to XML.Diese Eigenschaften werden von den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement> im <xref:System.Xml.Linq>\-Namespace verfügbar gemacht.  
  
 Wie im Thema [Übersicht über die WPF\-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md) erläutert, gibt es für jede dynamische Eigenschaft in derselben Klasse eine entsprechende öffentliche Standardeigenschaft oder \-methode.Diese Standardmember können für die Mehrzahl der Fälle eingesetzt werden. Die dynamischen Eigenschaften werden speziell für LINQ to XML\-Datenbindungsszenarios bereitgestellt.Weitere Informationen zu den Standardmembern dieser Klassen finden Sie in den Referenzthemen zu den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement>.  
  
 Die dynamischen Eigenschaften in diesem Abschnitt lassen sich hinsichtlich ihrer aufgelösten Werte in zwei Kategorien einteilen:  
  
-   einfache dynamische Eigenschaften, wie die `Value`\-Eigenschaften in den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement>, die einen einzelnen Wert ergeben  
  
-   indizierte Werte, wie die Eigenschaften [Elements](../designers/elements-xelement-dynamic-property.md) und [Descendants](../designers/descendants-xelement-dynamic-property.md) der <xref:System.Xml.Linq.XElement>\-Klasse, die einen Indexertyp ergeben.Damit der Indexertyp den gewünschten Wert bzw. die gewünschte Auflistung ergibt, muss ihm ein erweiterter Namensparameter übergeben werden.  
  
 Alle dynamischen Eigenschaften, die einen indizierten Wert des Typs <xref:System.Collections.Generic.IEnumerable%601> zurückgeben, arbeiten mit verzögerter Ausführung.Weitere Informationen über die verzögerte Ausführung finden Sie unter [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## Inhalt dieses Abschnitts  
  
|Thema|Beschreibung|  
|-----------|------------------|  
|[Dynamische Eigenschaften der 'Xattribute'\-Klasse](../designers/xattribute-class-dynamic-properties.md)|Enthält Details über die dynamischen Eigenschaften, die durch die Klasse <xref:System.Xml.Linq.XAttribute> verfügbar gemacht werden.|  
|[Dynamische Eigenschaften der 'XElement'\-Klasse](../designers/xelement-class-dynamic-properties.md)|Enthält Details über die dynamischen Eigenschaften, die durch die Klasse <xref:System.Xml.Linq.XElement> verfügbar gemacht werden.|  
  
## Referenz  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## Siehe auch  
 [WPF\-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Übersicht über die WPF\-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)