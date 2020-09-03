---
title: 'Gewusst wie: Starten des Debuggens von XSLT | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09471b9e62b758e4e02e054494ed108532bbd301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656329"
---
# <a name="how-to-start-debugging-xslt"></a>Gewusst wie: Starten des Debuggens von XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem XSLT-Debugger können XSLT-Stylesheets oder XSLT-Anwendungen debuggt werden. Beim Debuggen können Sie den Code zeilenweise ausführen, wobei Sie in einen Codeausdruck springen, einen Codeausdruck überspringen oder einen Codeausdruck wieder verlassen können, d. h., Sie haben die Möglichkeit, diesen Ausdruck bis zum Rücksprung auszuführen. Die bei der schrittweisen Codeausführung verwendeten Befehle im XSLT-Debugger sind mit denen in anderen Debuggern in Visual Studio identisch. Wenn Sie das Debuggen starten, öffnet der XSLT-Debugger Fenster, in denen das Eingabedokument und die XSLT-Ausgabe angezeigt werden.

## <a name="xml-editor"></a>XML-Editor
 Der Debugger kann im XML-Editor gestartet werden. Dadurch können Sie ein Stylesheet bereits beim Entwerfen debuggen.

#### <a name="to-start-debugging-from-a-style-sheet"></a>So starten Sie das Debuggen eines Stylesheets

1. Öffnen Sie das Stylesheet im XML-Editor.

2. Wählen Sie im **XML** -Menü **XSL debuggen** aus.

#### <a name="to-start-debugging-from-an-xml-input-document"></a>So starten Sie das Debuggen eines XML-Eingabedokuments

1. Öffnen Sie das XML-Dokument im XML-Editor.

2. Wählen Sie im **XML** -Menü **XSL debuggen** aus.

## <a name="xslt-from-other-languages"></a>XSLT aus anderen Sprachen
 Auch beim Debuggen einer Anwendung können Sie XSLT schrittweise ausführen. Wenn Sie die Taste F11 bei einem -Aufruf drücken, führt der Debugger den XSLT-Code schrittweise aus.

> [!NOTE]
> Die schrittweise Ausführung von XSLT aus der <xref:System.Xml.Xsl.XslTransform>-Klasse wird nicht unterstützt. Die <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse ist der einzige XSLT-Prozessor, der beim Debuggen die schrittweise Ausführung von XSLT unterstützt.

#### <a name="to-start-debugging-an-xslt-application"></a>So starten Sie das Debuggen einer XSLT-Anwendung

1. Legen Sie beim Instanziieren des <xref:System.Xml.Xsl.XslCompiledTransform>-Objekts im Code den `enableDebug`-Parameter auf `true` fest.

     Damit wird der XSLT-Prozessor angewiesen, dass beim Kompilieren des Codes Debuginformationen erstellt werden sollen.

2. Um den XSLT-Code schrittweise auszuführen, drücken Sie die Taste F11.

     Das XSLT-Stylesheet wird in einem neuen Dokumentfenster geladen, und der XSLT-Debugger wird gestartet.

     Alternativ können Sie dem Stylesheet einen Haltepunkt hinzufügen und die Anwendung ausführen.

### <a name="example"></a>Beispiel
 Im folgenden Beispiel wird ein C#-XSLT-Programm dargestellt. Darin wird veranschaulicht, wie das XSLT-Debuggen aktiviert wird.

```
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";
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

## <a name="see-also"></a>Weitere Informationen
 Exemplarische Vorgehensweise [: Debuggen einer XSLT-Stylesheet](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) - [Code Sprung Übersicht](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)
