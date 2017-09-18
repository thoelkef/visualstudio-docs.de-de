---
title: "CA3075: Unsichere DTD-Verarbeitung | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3075: Unsichere DTD-Verarbeitung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureDTDProcessing|  
|CheckId|CA3075|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## Ursache  
 Wenn Sie unsichere <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>\-Instanzen oder externe Entitätsquellen verweisen, kann der Parser unter Umständen nicht vertrauenswürdige Eingaben akzeptieren und Angreifern vertrauliche Informationen offenlegen.  
  
## Regelbeschreibung  
 Eine [Document Type Definition \(DTD\)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) ist eine von zwei Methoden, mit denen ein XML\-Parser die Gültigkeit eines Dokuments gemäß [World Wide Web Consortium \(W3C\) Extensible Markup Language \(XML\) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/) bestimmen kann. Diese Regel sucht Eigenschaften und Instanzen, die nicht vertrauenswürdige Daten akzeptieren, um Entwickler vor potenziellen [Veröffentlichung von Informationen](../Topic/Information%20Disclosure.md)\-Bedrohungen zu warnen, die zu [Denial\-of\-Service\-Angriffen \(DoS\)](../Topic/Denial%20of%20Service.md) führen können. Diese Regel wird  in folgenden Fällen ausgelöst:  
  
-   DtdProcessing wird in der <xref:System.Xml.XmlReader>\-Instanz aktiviert, die externe XML\-Entitäten mit <xref:System.Xml.XmlUrlResolver> auflöst.  
  
-   Die <xref:System.Xml.XmlNode.InnerXml%2A>\-Eigenschaft in XML wird festgelegt.  
  
-   Die <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>\-Eigenschaft wird auf „Parse“ festgelegt.  
  
-   Die Verarbeitung einer nicht vertrauenswürdigen Eingabe erfolgt mit <xref:System.Xml.XmlResolver> anstelle von <xref:System.Xml.XmlSecureResolver> .  
  
-   Die XmlReader.<xref:System.Xml.XmlReader.Create%2A>\-Methode wird mit einer unsicheren <xref:System.Xml.XmlReaderSettings> Instanz oder ohne Instanz aufgerufen.  
  
-   <xref:System.Xml.XmlReader> wird mit unsicheren Standardeinstellungen oder Werten erstellt.  
  
 In jedem dieser Fälle ist das Ergebnis identisch: Der Inhalt aus dem Dateisystem oder von Netzwerkfreigaben auf dem Computer, auf dem der XML\-Code verarbeitet wird, wird dem Angreifer offengelegt und kann dann als DoS\-Vektor verwendet werden.  
  
## Behandeln von Verstößen  
  
-   Alle XmlTextReader\-Ausnahmen müssen ordnungsgemäß abgefangen und verarbeitet werden, um die Offenlegung von Pfadinformationen zu vermeiden.  
  
-   Verwenden Sie <xref:System.Xml.XmlSecureResolver> , um die Ressourcen zu beschränken, auf die XmlTextReader zugreifen kann.  
  
-   Legen Sie die <xref:System.Xml.XmlResolver>\-Eigenschaft auf **null** fest, um zu verhindern, dass <xref:System.Xml.XmlReader> externe Ressourcen öffnen kann.  
  
-   Stellen Sie sicher, dass die <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A>\-Eigenschaft von <xref:System.Data.DataViewManager> von einer vertrauenswürdigen Quelle aus zugewiesen wird.  
  
 .NET 3.5 und früher  
  
-   Deaktivieren Sie die DTD\-Verarbeitung, wenn Sie mit nicht vertrauenswürdigen Quellen arbeiten, indem Sie die <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A>\-Eigenschaft auf  **true** festlegen.  
  
-   Die XmlTextReader\-Klasse verfügt über die Vererbungsanforderung „volle Vertrauenswürdigkeit“. Weitere Informationen finden Sie unter [Vererbungsanforderungen](http://msdn.microsoft.com/de-de/28b9adbb-8f08-4f10-b856-dbf59eb932d9).  
  
 .NET 4 und höher  
  
-   Verhindern Sie die Aktivierung von DtdProcessing, wenn Sie mit nicht vertrauenswürdigen Quellen arbeiten, indem Sie die DtdProcessing\-Eigenschaft auf [Nicht zulassen](https://msdn.microsoft.com/en-us/library/system.xml.dtdprocessing.aspx) oder „Ignorieren“ festlegen.  
  
-   Stellen Sie sicher, dass die Load\(\)\-Methode in allen InnerXml\-Fällen eine XmlReader\-Instanz annimmt.  
  
> [!NOTE]
>  Diese Regel meldet möglicherweise für einige gültige XmlSecureResolver\-Instanzen falsch positive Ergebnisse. Wir arbeiten an der Lösung dieses Problems bis Mitte 2016.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Regel aus dieser Warnung niemals, es sei denn, Sie sind ganz sicher, dass die Eingabe von einer vertrauenswürdigen Quelle stammt.  
  
## Pseudocodebeispiele  
  
### Verletzung  
  
```c#  
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
  
### Lösung  
  
```c#  
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
  
### Verletzung  
  
```c#  
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
  
### Lösung  
  
```c#  
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
  
### Verletzungen  
  
```c#  
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
  
```c#  
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
  
### Lösung  
  
```c#  
using System.Xml;   
  
public static void TestMethod(string xml)   
{   
    XmlDocument doc = new XmlDocument() { XmlResolver = null };   
    System.IO.StringReader sreader = new System.IO.StringReader(xml);   
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };   
    doc.Load(reader);   
}  
```  
  
### Verletzung  
  
```c#  
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
  
### Lösung  
  
```c#  
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
  
### Verletzung  
  
```c#  
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
  
### Lösung  
  
```c#  
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
  
### Verletzung  
  
```c#  
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };   
    }   
}  
```  
  
### Lösung  
  
```c#  
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance   
    }   
}  
```  
  
### Verletzungen  
  
```c#  
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
  
```c#  
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
  
```c#  
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
  
### Lösung  
  
```c#  
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