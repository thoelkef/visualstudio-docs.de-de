---
title: 'CA3077: Unsichere Verarbeitung in API-Design, XML-Dokument und XML-Textreader'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21c7d4fcf2ec1e16a225879b7feceef2a61a8161
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
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

-   <xref:System.Xml.XmlDocument> oder <xref:System.Xml.XmlTextReader> Klassen verwenden standardresolverwerte für die DTD-Verarbeitung.

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