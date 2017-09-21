---
title: "CA3077: Unsichere Verarbeitung in API-Design, XML-Dokument und XML-Textreader | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3077: Unsichere Verarbeitung in API-Design, XML-Dokument und XML-Textreader
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## Ursache  
 Beim Entwerfen einer von XMLDocument und XMLTextReader abgeleiteten API sollten Sie <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> berücksichtigen.  Das Verwenden unsicherer DTDProcessing\-Instanzen beim Verweisen auf externe Entitätsquellen bzw. bei deren Auflösung oder das Festlegen unsicherer Werte in XML\-Code kann zum Offenlegen von Informationen führen.  
  
## Regelbeschreibung  
 Eine [Document Type Definition \(DTD\)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) ist eine von zwei Methoden, mit denen ein XML\-Parser die Gültigkeit eines Dokuments gemäß [World Wide Web Consortium \(W3C\) Extensible Markup Language \(XML\) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/) bestimmen kann. Diese Regel sucht Eigenschaften und Instanzen, die nicht vertrauenswürdige Daten akzeptieren, um Entwickler vor potenziellen [Veröffentlichung von Informationen](../Topic/Information%20Disclosure.md)\-Bedrohungen zu warnen, die zu [Denial\-of\-Service\-Angriffen \(DoS\)](../Topic/Denial%20of%20Service.md) führen können. Diese Regel wird  in folgenden Fällen ausgelöst:  
  
-   <xref:System.Xml.XmlDocument>\- oder <xref:System.Xml.XmlTextReader>\-Klassen verwenden Standardresolverwerte für die DTD\-Verarbeitung.  
  
-   Für die abgeleiteten XmlDocument\- oder XmlTextReader\-Klassen wurde kein Konstruktor definiert oder für <xref:System.Xml.XmlResolver> wird kein sicherer Wert verwendet.  
  
## Behandeln von Verstößen  
  
-   Alle XmlTextReader\-Ausnahmen müssen ordnungsgemäß abgefangen und verarbeitet werden, um die Offenlegung von Pfadinformationen zu vermeiden.  
  
-   Verwenden Sie <xref:System.Xml.XmlSecureResolver> anstelle von XmlResolver , um die Ressourcen zu beschränken, auf die XmlTextReader zugreifen kann.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Regel aus dieser Warnung niemals, es sei denn, Sie sind ganz sicher, dass die Eingabe von einer vertrauenswürdigen Quelle stammt.  
  
## Pseudocodebeispiele  
  
### Verletzung  
  
```c#  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass () {} // warn   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2() // warn   
        {   
        }   
    }   
}  
```  
  
### Lösung  
  
```c#  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass ()    
        {   
            XmlResolver = null;   
        }   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2()    
        {   
               XmlResolver = null;   
        }   
    }   
}  
```