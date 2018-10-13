---
title: Dynamische Eigenschaften in LINQ to XML | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b16ff8a5969282f2c062c19fed84292f0755d0b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212419"
---
# <a name="linq-to-xml-dynamic-properties"></a>Dynamische Eigenschaften in LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser Abschnitt enthält Referenzinformationen zu den dynamischen Eigenschaften in LINQ to XML. Diese Eigenschaften werden von den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement>im <xref:System.Xml.Linq>-Namespace verfügbar gemacht.  
  
 Wie im Thema [Übersicht über die WPF-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md) erläutert, gibt es für jede dynamische Eigenschaft in derselben Klasse eine entsprechende öffentliche Standardeigenschaft oder -methode. Diese Standardmember können für die Mehrzahl der Fälle eingesetzt werden. Die dynamischen Eigenschaften werden speziell für LINQ to XML-Datenbindungsszenarien bereitgestellt. Weitere Informationen zu den Standardmembern dieser Klassen finden Sie in den Referenzthemen zu den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement>.  
  
 Die dynamischen Eigenschaften in diesem Abschnitt lassen sich hinsichtlich ihrer aufgelösten Werte in zwei Kategorien einteilen:  
  
-   einfache dynamische Eigenschaften, wie die `Value`-Eigenschaften in den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement>, die einen einzelnen Wert ergeben  
  
-   Indizierte Werte, wie die Eigenschaften [Elements](../designers/elements-xelement-dynamic-property.md) und [Descendants](../designers/descendants-xelement-dynamic-property.md) der <xref:System.Xml.Linq.XElement>-Klasse, die einen Indexertyp ergeben. Damit der Indexertyp den gewünschten Wert bzw. die gewünschte Auflistung ergibt, muss ihm ein erweiterter Namensparameter übergeben werden.  
  
 Alle dynamischen Eigenschaften, die einen indizierten Wert des Typs <xref:System.Collections.Generic.IEnumerable%601> zurückgeben, arbeiten mit verzögerter Ausführung. Weitere Informationen zur verzögerten Ausführung finden Sie unter [Einführung in LINQ-Abfragen (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Dynamische Eigenschaften der XAttribute-Klasse](../designers/xattribute-class-dynamic-properties.md)|Enthält Details über die dynamischen Eigenschaften, die durch die Klasse <xref:System.Xml.Linq.XAttribute> verfügbar gemacht werden.|  
|[Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)|Enthält Details über die dynamischen Eigenschaften, die durch die Klasse <xref:System.Xml.Linq.XElement> verfügbar gemacht werden.|  
  
## <a name="reference"></a>Referenz  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>Siehe auch  
 [WPF-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Übersicht über die WPF-Datenbindung mit LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduction to LINQ Queries (C#) (Einführung in LINQ-Abfragen (C#))](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)



