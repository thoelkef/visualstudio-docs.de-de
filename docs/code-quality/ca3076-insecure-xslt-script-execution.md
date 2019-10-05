---
title: 'CA3076: Unsichere XSLT-Skriptausführung.'
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c6c5df0109a8cff3cefcc308ea27077ef0fbe03
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237081"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Unsichere XSLT-Skriptausführung.

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Wenn Sie Extensible Stylesheets Language Transformations (XSLT) ungesichert in .NET-Anwendungen ausführen, könnte der Prozessor möglicherweise nicht vertrauenswürdige URI-Verweise auflösen, wodurch Angreifern sensible Informationen offengelegt werden könnten, was wiederum zu Denial-of-Service- und Cross-Site-Angriffen führen kann. Weitere Informationen finden Sie unter [XSLT-Sicherheitsüberlegungen (. net Guide)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Regelbeschreibung

**XSLT** ist ein W3C-Standard (World Wide Web Consortium) zum Transformieren von XML-Daten. XSLT wird in der Regel verwendet, um Stylesheets zum Transformieren von XML-Daten in andere Formate (z. b. html, Text mit fester Länge, durch Trennzeichen getrennten Text oder ein anderes XML-Format) zu schreiben. Dies ist zwar standardmäßig nicht zulässig, sie können die Option aber für Ihr Projekt aktivieren.

Um sicherzustellen, dass Sie keine Angriffsfläche verfügbar machen, wird diese Regel immer dann ausgelöst, wenn XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> empfängt unsichere Kombinations Instanzen von <xref:System.Xml.Xsl.XsltSettings> und <xref:System.Xml.XmlResolver>, wodurch die Verarbeitung bösartiger Skripts ermöglicht wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Ersetzen Sie das unsichere XsltSettings-Argument durch XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> oder mit einer-Instanz, die die Dokument Funktion und Skriptausführung deaktiviert hat.

- Ersetzen Sie das <xref:System.Xml.XmlResolver> -Argument durch „Null“ oder eine <xref:System.Xml.XmlSecureResolver> -Instanz.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie eine Regel aus dieser Warnung niemals, es sei denn, Sie sind ganz sicher, dass die Eingabe von einer vertrauenswürdigen Quelle stammt.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Verstoß, bei dem XsltSettings. treudxslt verwendet wird

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

### <a name="solution-that-uses-xsltsettingsdefault"></a>Projekt Mappe, die XsltSettings. default verwendet

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

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Verstoß&mdash;gegen Dokument Funktion und Skriptausführung nicht deaktiviert

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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Lösung&mdash;Deaktivieren der Dokument Funktion und Skriptausführung

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

## <a name="see-also"></a>Siehe auch

- [XSLT-Sicherheitsüberlegungen (. net-Leitfaden)](/dotnet/standard/data/xml/xslt-security-considerations)