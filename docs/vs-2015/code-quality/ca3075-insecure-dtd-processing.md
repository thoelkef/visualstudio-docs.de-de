---
title: 'CA3075: unsichere DTD-Verarbeitung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7cf9da2f295d94ac68c74039458f4cdbfda3ae5c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661624"
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
 Eine [Document Type Definition (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) ist eine von zwei Methoden, mit denen ein XML-Parser die Gültigkeit eines Dokuments gemäß  [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)bestimmen kann. Diese Regel sucht Eigenschaften und Instanzen, die nicht vertrauenswürdige Daten akzeptieren, um Entwickler vor potenziellen [Information Disclosure](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) -Bedrohungen zu warnen, die zu [Denial-of-Service-Angriffen (DoS)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) führen können. Diese Regel wird  in folgenden Fällen ausgelöst:

- DtdProcessing wird in der <xref:System.Xml.XmlReader> -Instanz aktiviert, die externe XML-Entitäten mit <xref:System.Xml.XmlUrlResolver>auflöst.

- Die <xref:System.Xml.XmlNode.InnerXml%2A> -Eigenschaft in XML wird festgelegt.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>-Eigenschaft ist auf "analysieren" festgelegt.

- Die Verarbeitung einer nicht vertrauenswürdigen Eingabe erfolgt mit <xref:System.Xml.XmlResolver> anstelle von <xref:System.Xml.XmlSecureResolver> .

- Der XmlReader. <xref:System.Xml.XmlReader.Create%2A> die Methode wird mit einer unsicheren <xref:System.Xml.XmlReaderSettings> Instanz oder gar keiner Instanz aufgerufen.

- <xref:System.Xml.XmlReader> mit unsicheren Standardeinstellungen oder-Werten erstellt wird.

  In jedem dieser Fälle ist das Ergebnis identisch: Der Inhalt aus dem Dateisystem oder von Netzwerkfreigaben auf dem Computer, auf dem der XML-Code verarbeitet wird, wird dem Angreifer offengelegt und kann dann als DoS-Vektor verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Alle XmlTextReader-Ausnahmen ordnungsgemäß erfassen und verarbeiten, um die Offenlegung von Pfadinformationen zu vermeiden.

- Verwenden Sie die  <xref:System.Xml.XmlSecureResolver>, um die Ressourcen einzuschränken, auf die der XmlTextReader zugreifen kann.

- Lassen Sie die  <xref:System.Xml.XmlReader> externe Ressourcen nicht zu öffnen, indem Sie die <xref:System.Xml.XmlResolver>-Eigenschaft auf **null**festlegen.

- Stellen Sie sicher, dass die <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> -Eigenschaft von <xref:System.Data.DataViewManager> von einer vertrauenswürdigen Quelle aus zugewiesen wird.

  .NET 3.5 und früher

- Deaktivieren Sie die DTD-Verarbeitung, wenn Sie mit nicht vertrauenswürdigen Quellen arbeiten, indem Sie die  <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A>-Eigenschaft auf **true** festlegen.

- Die XmlTextReader-Klasse verfügt über die Vererbungsanforderung „volle Vertrauenswürdigkeit“. Weitere Informationen finden Sie unter [Vererbungs Anforderungen](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) .

  .NET 4 und höher

- Verhindern Sie die Aktivierung von DtdProcessing, wenn Sie mit nicht vertrauenswürdigen Quellen arbeiten, indem Sie die DtdProcessing-Eigenschaft auf [Nicht zulassen](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx)oder „Ignorieren“ festlegen.

- Stellen Sie sicher, dass die Load()-Methode in allen InnerXml-Fällen eine XmlReader-Instanz annimmt.

> [!NOTE]
> Diese Regel meldet möglicherweise für einige gültige XmlSecureResolver-Instanzen falsch positive Ergebnisse. Wir arbeiten an der Lösung dieses Problems bis Mitte 2016.

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
