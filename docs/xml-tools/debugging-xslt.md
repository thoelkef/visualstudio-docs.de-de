---
title: Möglichkeiten zum Debuggen von XSLT-code
ms.date: 03/05/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 67ea95e3c52daed03acfe451f353edc039e1fecb
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043534"
---
# <a name="debugging-xslt"></a>Debugging von XSLT

Sie können XSLT-Code in Visual Studio debuggen. Die XSLT-Datei unterstützt das Festlegen von Haltepunkten, Anzeigen des XSLT-debugger, und so weiter. Der XSLT-Debugger kann zum Debuggen von XSLT-Stylesheets oder XSLT-Anwendungen verwendet werden.

Sie können eine Codezeile zu einem Zeitpunkt ausführen, durch Ausführen in Einzelschritten, überspringen oder beim Ausführen von Code. Die Befehle für die Code-stepping Funktionen von der XSLT-Debugger sind, dass die identisch mit denen für andere Visual Studio Debugger.

Wenn Sie das Debuggen starten, öffnet der XSLT-Debugger Fenster, in denen das Eingabedokument und die XSLT-Ausgabe angezeigt werden.

> [!NOTE]
> Der XSLT-Debugger ist nur in den Editionen Professional und Enterprise von Visual Studio verfügbar.

## <a name="debug-from-the-xml-editor"></a>Debuggen Sie im XML-Editor

Sie können den Debugger starten, wenn man entweder ein Stylesheet oder eine XML-Eingabedatei im Editor zu öffnen. Dadurch können Sie das Debuggen, wie Sie das Stylesheet entwerfen.

1. Öffnen Sie das Stylesheet oder eine XML-Datei in Visual Studio.

1. Wählen Sie **XSLT Debuggen starten** aus der **XML** Menü, oder drücken Sie **Alt**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Debuggen Sie über eine app, die mithilfe von XSLT

Sie können beim Debuggen einer Anwendung XSLT schrittweise. Beim Drücken **F11** auf eine <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> Aufruf des Debuggers schrittweise den XSLT-Code.

> [!NOTE]
> Die schrittweise Ausführung von XSLT aus der <xref:System.Xml.Xsl.XslTransform>-Klasse wird nicht unterstützt. Die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse ist der einzige XSLT-Prozessor, der beim Debuggen die schrittweise Ausführung von XSLT unterstützt.

### <a name="to-start-debugging-an-xslt-application"></a>So starten Sie das Debuggen einer XSLT-Anwendung

1. Legen Sie beim Instanziieren des <xref:System.Xml.Xsl.XslCompiledTransform>-Objekts im Code den `enableDebug`-Parameter auf `true` fest. Damit wird der XSLT-Prozessor angewiesen, dass beim Kompilieren des Codes Debuginformationen erstellt werden sollen.

1. Drücken Sie **F11** um in den XSLT-Code zu springen.

   XSLT-Stylesheet wird in einem neuen Dokumentfenster geladen, und der XSLT-Debugger wird gestartet.

   Alternativ können Sie dem Stylesheet einen Haltepunkt hinzufügen und die Anwendung ausführen.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein C#-XSLT-Programm dargestellt. Darin wird veranschaulicht, wie das XSLT-Debuggen aktiviert wird.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>XSLT-Profiler

Die [XSLT-Profiler](../xml-tools/xslt-profiler.md) ist ein Tool, mit dem Entwickler, die messen, auswerten und leistungsbezogener Probleme im XSLT-Code durch das Erstellen von ausführlichen XSLT-Leistungsberichten. Weitere Informationen finden Sie unter [XSLT-Profiler](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Erster Einblick in die Visual Studio-debugger](../debugger/debugger-feature-tour.md)
- [Debuggrundlagen: Haltepunkte](../debugger/using-breakpoints.md)
