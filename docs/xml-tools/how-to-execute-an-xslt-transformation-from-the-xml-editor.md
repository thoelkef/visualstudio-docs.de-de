---
title: 'Gewusst wie: Ausführen einer XSLT-Transformation im XML-Editor'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 892f82d64bb022c20c786a996bf9f89cf557b4c2
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548281"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Vorgehensweise: Ausführen eine XSLT-Transformation im XML-Editor

Mit dem XML-Editor können Sie einem XML-Dokument ein XSLT-Stylesheet zuordnen, die Transformation ausführen und die Ausgabe anzeigen. Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

Die **Ausgabe** Eigenschaft gibt den Dateinamen für die Ausgabe. Wenn die **Ausgabe** Eigenschaft leer ist, wird ein Dateiname in einem temporären Verzeichnis generiert. Die Dateierweiterung basiert auf der `xsl:output` -Element im Stylesheet and kann sein. *XML*,. *TXT* oder. *Htm*.

Wenn die **Ausgabe** Eigenschaft gibt einen Dateinamen mit einer. *Htm* oder. *HTML* -Erweiterung der XSLT-Ausgabe wird in der Vorschau angezeigten mit [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer. Bei allen anderen Dateierweiterungen wird der von [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]-Visual Studio ausgewählte Standard-Editor verwendet. Wenn z. B. die Erweiterung der Ausgabedatei lautet. *Xml*, verwendet Visual Studio der XML-Editor.

## <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>So führen Sie eine XSLT-Transformation in einem XML-Dokument aus

1.  Öffnen Sie ein XML-Dokument im XML-Editor.

2.  Ordnen Sie dem XML-Dokument ein XSLT-Stylesheet zu.

    -   Fügen Sie dem XML-Dokument eine `xml-stylesheet`-Verarbeitungsanweisung hinzu. Fügen Sie z. B. dem Dokumentprolog folgende Zeile `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` hinzu.

         - oder - 

    -   Fügen Sie dem XSLT-Stylesheet mithilfe der **Eigenschaften** Fenster. Im Dokument **Fenster "Eigenschaften"**, klicken Sie auf die **Durchsuchen** Schaltfläche für die **Stylesheet** Feld Wählen Sie die XSLT-Stylesheet, und klicken Sie auf **öffnen**.

3.  Klicken Sie auf die **ShowXSL Ausgabe** Schaltfläche auf der **XML-Editor** Symbolleiste.

    > [!NOTE]
    > Wenn dem XML-Dokument kein Stylesheet zugeordnet ist, werden Sie in einem Dialogfeld aufgefordert, das zu verwendende Stylesheet bereitzustellen.
    >
    >  Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

## <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>So führen Sie eine XSLT-Transformation in einem XSLT-Stylesheet aus

1.  Öffnen Sie ein XSLT-Stylesheet im XML-Editor.

2.  Geben Sie ein XML-Dokument in der **Eingabe** Feld des Dokuments **Eigenschaften** Fenster.

    > [!NOTE]
    > Das XML-Dokument ist das für die Transformation verwendete Eingabedokument. Wenn ein Dokument nicht angegeben wird, wenn die XSLT-Transformation gestartet wird, die **Datei öffnen** Dialogfeld wird angezeigt, und Sie können nun ein Dokument angeben.

3.  Klicken Sie auf die **ShowXSLT Ausgabe** Schaltfläche auf der **XML-Editor** Symbolleiste.

     Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

## <a name="to-provide-a-different-output-file-name"></a>So stellen Sie einen anderen Ausgabedateinamen bereit

1.  Geben Sie einen Namen in der **Ausgabe** Feld des Dokuments **Eigenschaften** Fenster.

2.  Klicken Sie auf die **ShowXSLT Ausgabe** Schaltfläche auf der **XML-Editor** Symbolleiste.

     Aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt, und im Ausgabefenster verwendete Editor hängt von der Erweiterung Ihrer **Ausgabe** -Dokumenteigenschaft.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)