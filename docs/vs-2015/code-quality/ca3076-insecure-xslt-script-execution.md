---
title: 'CA3076: Unsichere XSLT-Skriptausführung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d814c71e7ce1cbde850357feab9251ee58fd1358
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590333"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Unsichere XSLT-Skriptausführung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA3076: unsichere XSLT-Skriptausführung](https://docs.microsoft.com/visualstudio/code-quality/ca3076-insecure-xslt-script-execution).

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Wenn Sie [Extensible Stylesheets Language Transformations (XSLT)](https://support.microsoft.com/en-us/kb/313997) ungesichert in .NET-Anwendungen ausführen, könnte der Prozessor möglicherweise [nicht vertrauenswürdige URI-Verweise auflösen](http://msdn.microsoft.com/en-us/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) , wodurch Angreifern sensible Informationen offengelegt werden könnten, was wiederum zu Denial-of-Service- und Cross-Site-Angriffen führen kann.

## <a name="rule-description"></a>Regelbeschreibung
 [XSLT](http://msdn.microsoft.com/en-us/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) ist ein W3C-Standard (World Wide Web Consortium) zum Transformieren von XML-Daten. XSLT wird in der Regel verwendet, um Stylesheets zum Transformieren von XML-Daten in andere Formate (z. B.in HTML, Text fester Länge, durch Trennzeichen getrennter Text oder ein anderes XML-Format) zu schreiben. Dies ist zwar standardmäßig nicht zulässig, sie können die Option aber für Ihr Projekt aktivieren.

 Um sicherzustellen, können Sie keine Angriffsfläche, mit dieser Regel wird ausgelöst, wenn die "XslCompiledTransform".<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Unsichere Kombinationen aus empfängt <xref:System.Xml.Xsl.XsltSettings> und <xref:System.Xml.XmlResolver>, wodurch die Verarbeitung von bösartigen Skripts.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

-   Ersetzen Sie das unsichere XsltSettings-Argument durch XsltSettings an.<xref:System.Xml.Xsl.XsltSettings.Default%2A> oder mit einer Instanz, die Dokument-Funktion und Skript die Ausführung deaktiviert wurde.

-   Ersetzen Sie das <xref:System.Xml.XmlResolver> -Argument durch „Null“ oder eine <xref:System.Xml.XmlSecureResolver> -Instanz.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Regel aus dieser Warnung niemals, es sei denn, Sie sind ganz sicher, dass die Eingabe von einer vertrauenswürdigen Quelle stammt.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation"></a>Verletzung

```csharp
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

### <a name="solution"></a>Lösung

```csharp
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

### <a name="violation"></a>Verletzung

```csharp
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

### <a name="solution"></a>Lösung

```csharp
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



