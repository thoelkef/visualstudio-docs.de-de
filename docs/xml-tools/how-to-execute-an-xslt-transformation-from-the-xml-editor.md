---
title: 'Vorgehensweise: Ausführen einer XSLT-Transformation im XML-Editor'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 742e78eca883dd2e9e9fc5ecfa8ec5381f003b61
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987569"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Vorgehensweise: Ausführen einer XSLT-Transformations im XML-Editor

Mit dem XML-Editor können Sie einem XML-Dokument ein XSLT-Stylesheet zuordnen, die Transformation ausführen und die Ausgabe anzeigen. Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

Die **Ausgabe** Eigenschaft gibt den Dateinamen für die Ausgabe an. Wenn die **Ausgabe** -Eigenschaft leer ist, ein Dateinamen in einem temporären Verzeichnis generiert. Die Dateierweiterung basiert auf der `xsl:output` -Element im Stylesheet and kann. *XML*,. *TXT* oder. *Htm*.

Wenn die **Ausgabe** Eigenschaft gibt einen Dateinamen mit einer. *Htm* oder. *HTML* Erweiterung der XSLT-Ausgabe wird in der Vorschau angezeigten mit [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer. Bei allen anderen Dateierweiterungen wird der von [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]-Visual Studio ausgewählte Standard-Editor verwendet. Wenn beispielsweise die Dateierweiterung ist. *Xml*, verwendet der XML-Editor von Visual Studio.

## <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>So führen Sie eine XSLT-Transformation in einem XML-Dokument aus

1.  Öffnen Sie ein XML-Dokument im XML-Editor.

2.  Ordnen Sie dem XML-Dokument ein XSLT-Stylesheet zu.

    -   Fügen Sie dem XML-Dokument eine `xml-stylesheet`-Verarbeitungsanweisung hinzu. Fügen Sie z. B. dem Dokumentprolog folgende Zeile `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` hinzu.

         - oder - 

    -   Fügen Sie dem XSLT-Stylesheet mithilfe der **Eigenschaften** Fenster. Im Dokument **Fenster "Eigenschaften"**, klicken Sie auf die **Durchsuchen** Schaltfläche der **Stylesheet** Feld, wählen Sie das XSLT-Stylesheet, und klicken Sie auf **öffnen**.

3.  Klicken Sie auf die **ShowXSL Ausgabe** Schaltfläche der **XML-Editor** Symbolleiste.

    > [!NOTE]
    > Wenn dem XML-Dokument kein Stylesheet zugeordnet ist, werden Sie in einem Dialogfeld aufgefordert, das zu verwendende Stylesheet bereitzustellen.
    >
    >  Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

## <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>So führen Sie eine XSLT-Transformation in einem XSLT-Stylesheet aus

1.  Öffnen Sie ein XSLT-Stylesheet im XML-Editor.

2.  Geben Sie eine XML-Dokument in der **Eingabe** Feld des Dokuments **Eigenschaften** Fenster.

    > [!NOTE]
    > Das XML-Dokument ist das für die Transformation verwendete Eingabedokument. Wenn ein Dokument nicht angegeben wird, wenn die XSLT-Transformation gestartet wird, die **Datei öffnen** Dialogfeld wird angezeigt, und Sie können ein Dokument zu diesem Zeitpunkt angeben.

3.  Klicken Sie auf die **ShowXSLT Ausgabe** Schaltfläche der **XML-Editor** Symbolleiste.

     Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

## <a name="to-provide-a-different-output-file-name"></a>So stellen Sie einen anderen Ausgabedateinamen bereit

1.  Geben Sie einen Namen in der **Ausgabe** Feld des Dokuments **Eigenschaften** Fenster.

2.  Klicken Sie auf die **ShowXSLT Ausgabe** Schaltfläche der **XML-Editor** Symbolleiste.

     Die resultierende Ausgabe aus der XSLT-Transformation in einem neuen Dokumentfenster angezeigt wird, und im Ausgabefenster verwendete Editor hängt von der Erweiterungs der Ihre **Ausgabe** -Dokumenteigenschaft.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)