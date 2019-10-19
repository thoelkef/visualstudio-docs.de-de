---
title: 'Gewusst wie: Ausführen einer XSLT-Transformation im XML-Editor | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b305d88779603b374e5f95842d7a5271a657268
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666533"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Gewusst wie: Ausführen einer XSLT-Transformation im XML-Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem XML-Editor können Sie einem XML-Dokument ein XSLT-Stylesheet zuordnen, die Transformation ausführen und die Ausgabe anzeigen. Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

 Die **Output** -Eigenschaft gibt den Dateinamen für die Ausgabe an. Wenn die **Output** -Eigenschaft leer ist, wird ein Dateiname in Ihrem temporären Verzeichnis generiert. Die Dateierweiterung basiert auf dem `xsl:output`-Element im Stylesheet and kann XML, TXT oder HTM sein.

 Wenn die **Output** -Eigenschaft einen Dateinamen mit der Erweiterung. htm oder. html angibt, wird die XSLT-Ausgabe mit [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer in der Vorschau angezeigt. Bei allen anderen Dateierweiterungen wird der von [!INCLUDE[msCoName](../includes/msconame-md.md)]-Visual Studio ausgewählte Standard-Editor verwendet. Bei Dateien mit der Erweiterung XML wird beispielsweise von Visual Studio der XML-Editor verwendet.

### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>So führen Sie eine XSLT-Transformation in einem XML-Dokument aus

1. Öffnen Sie ein XML-Dokument im XML-Editor.

2. Ordnen Sie dem XML-Dokument ein XSLT-Stylesheet zu.

    - Fügen Sie dem XML-Dokument eine `xml-stylesheet`-Verarbeitungsanweisung hinzu. Fügen Sie z. B. dem Dokumentprolog folgende Zeile `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` hinzu.

         - oder -

    - Fügen Sie das XSLT-Stylesheet mithilfe des Fensters **Eigenschaften** hinzu. Klicken Sie im **Fenster Dokumenteigenschaften**auf die Schaltfläche **Durchsuchen** für das **Stylesheet** -Feld, wählen Sie das XSLT-Stylesheet aus, und klicken Sie auf **Öffnen**.

3. Klicken Sie auf der Symbolleiste des XML- **Editors** auf die Schaltfläche **ShowXSL Output** .

    > [!NOTE]
    > Wenn dem XML-Dokument kein Stylesheet zugeordnet ist, werden Sie in einem Dialogfeld aufgefordert, das zu verwendende Stylesheet bereitzustellen.
    >
    >  Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>So führen Sie eine XSLT-Transformation in einem XSLT-Stylesheet aus

1. Öffnen Sie ein XSLT-Stylesheet im XML-Editor.

2. Geben Sie im Fenster "Dokument **Eigenschaften** " im **Eingabe** Feld ein XML-Dokument an.

    > [!NOTE]
    > Das XML-Dokument ist das für die Transformation verwendete Eingabedokument. Wenn ein Dokument beim Starten der XSLT-Transformation nicht angegeben wird, wird das Dialogfeld **Datei öffnen** angezeigt, und Sie können ein Dokument zu diesem Zeitpunkt angeben.

3. Klicken Sie auf der Symbolleiste des XML- **Editors** auf die Schaltfläche **ShowXSLT Output** .

     Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

### <a name="to-provide-a-different-output-file-name"></a>So stellen Sie einen anderen Ausgabedateinamen bereit

1. Geben Sie im Feld **Ausgabe** des Fensters Dokument **Eigenschaften** einen Dateinamen an.

2. Klicken Sie auf der Symbolleiste des XML- **Editors** auf die Schaltfläche **ShowXSLT Output** .

     Die resultierende Ausgabe aus der XSLT-Transformation wird in einem neuen Dokument Fenster angezeigt, und der im Ausgabefenster verwendete Editor hängt von der Dateierweiterung der **Ausgabe** Dokument Eigenschaft ab.

## <a name="see-also"></a>Siehe auch
 [XML-Editor](../xml-tools/xml-editor.md)
