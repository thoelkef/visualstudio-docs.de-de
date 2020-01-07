---
title: Möglichkeiten zum Debuggen von XSLT-Code
ms.date: 03/05/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: f6f4a1ce60f04bcea6e21b52db9347a95292dab2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592853"
---
# <a name="debugging-xslt"></a>Debugging von XSLT

Sie können XSLT-Code in Visual Studio debuggen. Der XSLT-Debugger unterstützt das Festlegen von Breakpoints, das Anzeigen von XSLT-Ausführungs Zuständen usw. Der XSLT-Debugger kann zum Debuggen von XSLT-Stylesheets oder XSLT-Anwendungen verwendet werden.

Sie können Codezeilen Weise ausführen, indem Sie den Code schrittweise ausführen, schrittweise ausführen oder den Code schrittweise ausführen. Die Befehle zum Verwenden der Code-Step-Funktionalität des XSLT-Debuggers sind identisch mit denen für die anderen Visual Studio-Debugger.

Wenn Sie das Debuggen starten, öffnet der XSLT-Debugger Fenster, in denen das Eingabedokument und die XSLT-Ausgabe angezeigt werden.

> [!NOTE]
> Der XSLT-Debugger ist nur in den Editionen Professional und Enterprise von Visual Studio verfügbar.

## <a name="debug-from-the-xml-editor"></a>Debuggen aus dem XML-Editor

Sie können den Debugger starten, wenn Sie entweder ein Stylesheet oder eine XML-Eingabedatei im Editor geöffnet haben. Auf diese Weise können Sie beim Entwerfen des Stylesheets debuggen.

1. Öffnen Sie das Stylesheet oder die XML-Datei in Visual Studio.

1. Wählen Sie im **XML** -Menü **XSLT-Debuggen starten** aus, oder drücken Sie **alt**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Debuggen aus einer APP, die XSLT verwendet

Beim Debuggen einer Anwendung können Sie XSLT schrittweise ausführen. Wenn Sie bei einem <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>-Befehl **F11** drücken, kann der Debugger den XSLT-Code schrittweise ausführen.

> [!NOTE]
> Die schrittweise Ausführung von XSLT aus der <xref:System.Xml.Xsl.XslTransform>-Klasse wird nicht unterstützt. Die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse ist der einzige XSLT-Prozessor, der beim Debuggen die schrittweise Ausführung von XSLT unterstützt.

### <a name="to-start-debugging-an-xslt-application"></a>So starten Sie das Debuggen einer XSLT-Anwendung

1. Legen Sie beim Instanziieren des <xref:System.Xml.Xsl.XslCompiledTransform>-Objekts im Code den `enableDebug`-Parameter auf `true` fest. Damit wird der XSLT-Prozessor angewiesen, dass beim Kompilieren des Codes Debuginformationen erstellt werden sollen.

1. Drücken Sie **F11** , um den XSLT-Code schrittweise durchlaufen.

   Das XSLT-Stylesheet wird in einem neuen Dokument Fenster geladen, und der XSLT-Debugger wird gestartet.

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
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>XSLT-Profiler

Der [XSLT-Profiler](../xml-tools/xslt-profiler.md) ist ein Tool, mit dem Entwickler leistungsbezogene Probleme im XSLT-Code Messen, auswerten und beheben können, indem Sie ausführliche XSLT-Leistungsberichte erstellen. Weitere Informationen finden Sie unter [XSLT-Profiler](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Betrachten Sie zuerst den Visual Studio-Debugger.](../debugger/debugger-feature-tour.md)
- [Grundlagen zum Debugging: Breakpoints](../debugger/using-breakpoints.md)
