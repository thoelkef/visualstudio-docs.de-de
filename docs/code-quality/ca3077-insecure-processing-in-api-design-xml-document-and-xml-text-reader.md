---
title: 'CA3077: Unsichere Verarbeitung in API-Design, XML-Dokument und XML-Text-Reader | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e3e23441a0e4e03f2f7829c24513fd7cfce5eea
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Unsichere Verarbeitung in API-Design, XML-Dokument und XML-Textreader
|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Beim Entwerfen einer von XMLDocument und XMLTextReader abgeleiteten API sollten Sie <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>berücksichtigen.  Das Verwenden unsicherer DTDProcessing-Instanzen beim Verweisen auf externe Entitätsquellen bzw. bei deren Auflösung oder das Festlegen unsicherer Werte in XML-Code kann zum Offenlegen von Informationen führen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein *Document Type Definition (DTD)* ist einer von zwei Methoden, die ein XML-Parser, die Gültigkeit eines Dokuments bestimmen kann gemäß der [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Diese Regel sucht Eigenschaften und Instanzen, die nicht vertrauenswürdige Daten akzeptieren, um Entwickler vor potenziellen [Information Disclosure](/dotnet/framework/wcf/feature-details/information-disclosure) -Bedrohungen zu warnen, die zu [Denial-of-Service-Angriffen (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) führen können. Diese Regel wird  in folgenden Fällen ausgelöst:  
  
-   <xref:System.Xml.XmlDocument>oder <xref:System.Xml.XmlTextReader> Klassen verwenden standardresolverwerte für die DTD-Verarbeitung.  
  
-   Für die abgeleiteten XmlDocument- oder XmlTextReader-Klassen wurde kein Konstruktor definiert oder für <xref:System.Xml.XmlResolver>wird kein sicherer Wert verwendet.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
  
-   Abgefangen und verarbeitet alle XmlTextReader-Ausnahmen müssen ordnungsgemäß zur Offenlegung von Pfadinformationen zu vermeiden.  
  
-   Verwendung <xref:System.Xml.XmlSecureResolver>anstelle von XmlResolver, um die Ressourcen zu beschränken, die XmlTextReader zugreifen kann.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Regel aus dieser Warnung niemals, es sei denn, Sie sind ganz sicher, dass die Eingabe von einer vertrauenswürdigen Quelle stammt.  
  
## <a name="pseudo-code-examples"></a>Pseudocodebeispiele  
  
### <a name="violation"></a>Verletzung  
  
```csharp  
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
  
### <a name="solution"></a>Lösung  
  
```csharp  
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