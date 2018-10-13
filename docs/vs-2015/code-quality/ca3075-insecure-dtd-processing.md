---
title: 'CA3075: Unsichere DTD-Verarbeitung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b201631d86d0fd36a0f35d2842400473abf5fc3a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201577"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Unsichere DTD-Verarbeitung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Wenn Sie unsichere <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> -Instanzen oder externe Entitätsquellen verweisen, kann der Parser unter Umständen nicht vertrauenswürdige Eingaben akzeptieren und Angreifern vertrauliche Informationen offenlegen.

## <a name="rule-description"></a>Regelbeschreibung
 Eine [Document Type Definition (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) ist eine von zwei Methoden, mit denen ein XML-Parser die Gültigkeit eines Dokuments gemäß  [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)bestimmen kann. Diese Regel sucht Eigenschaften und Instanzen, die nicht vertrauenswürdige Daten akzeptieren, um Entwickler vor potenziellen [Information Disclosure](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) -Bedrohungen zu warnen, die zu [Denial-of-Service-Angriffen (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) führen können. Diese Regel wird  in folgenden Fällen ausgelöst:

-   DtdProcessing wird in der <xref:System.Xml.XmlReader> -Instanz aktiviert, die externe XML-Entitäten mit <xref:System.Xml.XmlUrlResolver>auflöst.

-   Die <xref:System.Xml.XmlNode.InnerXml%2A> -Eigenschaft in XML wird festgelegt.

-   <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> Analyse wird die Eigenschaft festgelegt.

-   Die Verarbeitung einer nicht vertrauenswürdigen Eingabe erfolgt mit <xref:System.Xml.XmlResolver> anstelle von <xref:System.Xml.XmlSecureResolver> .

-   Der XmlReader.<xref:System.Xml.XmlReader.Create%2A> Methode wird aufgerufen, mit einer unsicheren <xref:System.Xml.XmlReaderSettings> Instanz oder ohne Instanz.

-   <xref:System.Xml.XmlReader> wird mit unsicheren Standardeinstellungen oder Werten erstellt.

 In jedem dieser Fälle ist das Ergebnis identisch: Der Inhalt aus dem Dateisystem oder von Netzwerkfreigaben auf dem Computer, auf dem der XML-Code verarbeitet wird, wird dem Angreifer offengelegt und kann dann als DoS-Vektor verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

-   Fangen Sie ab und verarbeiten Sie alle XmlTextReader-Ausnahmen ordnungsgemäß, um die Offenlegung von Pfadinformationen zu vermeiden.

-   Verwenden der <xref:System.Xml.XmlSecureResolver> die Ressourcen zu beschränken, die die XmlTextReader zugreifen kann.

-   Erlauben Sie keine der <xref:System.Xml.XmlReader> keine externen Ressourcen öffnen die <xref:System.Xml.XmlResolver> Eigenschaft **null**.

-   Stellen Sie sicher, dass die <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> -Eigenschaft von <xref:System.Data.DataViewManager> von einer vertrauenswürdigen Quelle aus zugewiesen wird.

 .NET 3.5 und früher

-   Deaktivieren Sie die DTD-Verarbeitung, wenn Sie mit nicht vertrauenswürdigen Quellen arbeiten, indem Sie festlegen, werden die <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> Eigenschaft **"true"** .

-   Die XmlTextReader-Klasse verfügt über die Vererbungsanforderung „volle Vertrauenswürdigkeit“. Finden Sie unter [Vererbungsanforderungen](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) für Weitere Informationen.

 .NET 4 und höher

-   Verhindern Sie die Aktivierung von DtdProcessing, wenn Sie mit nicht vertrauenswürdigen Quellen arbeiten, indem Sie die DtdProcessing-Eigenschaft auf [Nicht zulassen](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx)oder „Ignorieren“ festlegen.

-   Stellen Sie sicher, dass die Load()-Methode in allen InnerXml-Fällen eine XmlReader-Instanz annimmt.

> [!NOTE]
>  Diese Regel meldet möglicherweise für einige gültige XmlSecureResolver-Instanzen falsch positive Ergebnisse. Wir arbeiten an der Lösung dieses Problems bis Mitte 2016.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Regel aus dieser Warnung niemals, es sei denn, Sie sind ganz sicher, dass die Eingabe von einer vertrauenswürdigen Quelle stammt.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Lösung

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>Verletzung

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Lösung

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>Verletzungen

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Lösung

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
    doc.Load(reader);
}
```

### <a name="violation"></a>Verletzung

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Lösung

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>Verletzung

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Lösung

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>Verletzung

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Lösung

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>Verletzungen

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Lösung

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```



