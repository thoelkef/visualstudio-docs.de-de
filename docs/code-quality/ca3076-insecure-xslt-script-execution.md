---
title: "CA3076: Unsichere XSLT-Skriptausf&#252;hrung | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3076: Unsichere XSLT-Skriptausf&#252;hrung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## Ursache  
 Wenn Sie [Extensible Stylesheets Language Transformations \(XSLT\)](https://support.microsoft.com/en-us/kb/313997) ungesichert in .NET\-Anwendungen ausführen, könnte der Prozessor möglicherweise [nicht vertrauenswürdige URI\-Verweise auflösen](http://msdn.microsoft.com/de-de/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a), wodurch Angreifern sensible Informationen offengelegt werden könnten, was wiederum zu Denial\-of\-Service\- und Cross\-Site\-Angriffen führen kann.  
  
## Regelbeschreibung  
 [XSLT](http://msdn.microsoft.com/de-de/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) ist ein W3C\-Standard \(World Wide Web Consortium\) zum Transformieren von XML\-Daten. XSLT wird in der Regel verwendet, um Stylesheets zum Transformieren von XML\-Daten in andere Formate \(z. B.in HTML, Text fester Länge, durch Trennzeichen getrennter Text oder ein anderes XML\-Format\) zu schreiben. Dies ist zwar standardmäßig nicht zulässig, sie können die Option aber für Ihr Projekt aktivieren.  
  
 Um sicherzustellen, dass Sie keine Angriffsfläche bieten, wird diese Regel jedes Mal dann ausgelöst, wenn XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> unsichere Kombinationen aus <xref:System.Xml.Xsl.XsltSettings> und <xref:System.Xml.XmlResolver> empfängt, die die Verarbeitung von bösartigen Skripts zulassen.  
  
## Behandeln von Verstößen  
  
-   Ersetzen Sie das unsichere XsltSettings\-Argument durch XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> oder durch eine Instanz, bei der Dokumentfunktion und Skriptausführung deaktiviert wurden.  
  
-   Ersetzen Sie das <xref:System.Xml.XmlResolver>\-Argument durch „Null“ oder eine <xref:System.Xml.XmlSecureResolver>\-Instanz.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Regel aus dieser Warnung niemals, es sei denn, Sie sind ganz sicher, dass die Eingabe von einer vertrauenswürdigen Quelle stammt.  
  
## Pseudocodebeispiele  
  
### Verletzung  
  
```c#  
using System.Xml;  
using System.Xml.Xsl;  
  
namespace TestNamespace   
{   
    class TestClass   
    {  
         void TestMethod()   
        {    
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
             var settings = XsltSettings.TrustedXslt;   
             var resolver = new XmlUrlResolver();   
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn   
        }  
    }   
}   
```  
  
### Lösung  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        void TestMethod()   
        {   
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
            var settings = XsltSettings.Default;   
            var resolver = new XmlUrlResolver();   
            xslCompiledTransform.Load("testStylesheet", settings, resolver);   
        }   
    }   
}  
```  
  
### Verletzung  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod(XsltSettings settings)   
        {   
            try   
            {   
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
                var resolver = new XmlUrlResolver();   
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn   
            }   
            catch { throw; }   
            finally { }   
        }   
    }   
}  
```  
  
### Lösung  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod(XsltSettings settings)   
        {   
            try   
            {   
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
                settings.EnableDocumentFunction = false;   
                settings.EnableScript = false;   
                var resolver = new XmlUrlResolver();   
                xslCompiledTransform.Load("testStylesheet", settings, resolver);   
            }   
            catch { throw; }   
            finally { }   
        }   
    }   
}  
```