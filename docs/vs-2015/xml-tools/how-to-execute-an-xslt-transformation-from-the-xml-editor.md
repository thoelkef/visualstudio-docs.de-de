---
title: 'Vorgehensweise: Ausführen eine XSLT-Transformation im XML-Editor | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7899c2c7816d926185958acc1eb9fb2e066a9a16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522246"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Gewusst wie: Ausführen einer XSLT-Transformation im XML-Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [wie: Ausführen einer XSLT-Transformation im XML-Editor](https://docs.microsoft.com/visualstudio/xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor).  
  
  
Mit dem XML-Editor können Sie einem XML-Dokument ein XSLT-Stylesheet zuordnen, die Transformation ausführen und die Ausgabe anzeigen. Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.  
  
 Die **Ausgabe** Eigenschaft gibt den Dateinamen für die Ausgabe an. Wenn die **Ausgabe** -Eigenschaft leer ist, ein Dateinamen in einem temporären Verzeichnis generiert. Die Dateierweiterung basiert auf dem `xsl:output`-Element im Stylesheet and kann XML, TXT oder HTM sein.  
  
 Wenn die **Ausgabe** Eigenschaft gibt einen Dateinamen mit einer HTM- oder HTML-Erweiterung, die XSLT-Ausgabe ist eine Vorschau mit [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer. Bei allen anderen Dateierweiterungen wird der von [!INCLUDE[msCoName](../includes/msconame-md.md)]-Visual Studio ausgewählte Standard-Editor verwendet. Bei Dateien mit der Erweiterung XML wird beispielsweise von Visual Studio der XML-Editor verwendet.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>So führen Sie eine XSLT-Transformation in einem XML-Dokument aus  
  
1.  Öffnen Sie ein XML-Dokument im XML-Editor.  
  
2.  Ordnen Sie dem XML-Dokument ein XSLT-Stylesheet zu.  
  
    -   Fügen Sie dem XML-Dokument eine `xml-stylesheet`-Verarbeitungsanweisung hinzu. Fügen Sie z. B. dem Dokumentprolog folgende Zeile `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` hinzu.  
  
         - oder -   
  
    -   Fügen Sie dem XSLT-Stylesheet mithilfe der **Eigenschaften** Fenster. Im Dokument **Fenster "Eigenschaften"**, klicken Sie auf die **Durchsuchen** Schaltfläche der **Stylesheet** Feld, wählen Sie das XSLT-Stylesheet, und klicken Sie auf **öffnen**.  
  
3.  Klicken Sie auf die **ShowXSL Ausgabe** Schaltfläche der **XML-Editor** Symbolleiste.  
  
    > [!NOTE]
    >  Wenn dem XML-Dokument kein Stylesheet zugeordnet ist, werden Sie in einem Dialogfeld aufgefordert, das zu verwendende Stylesheet bereitzustellen.  
    >   
    >  Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>So führen Sie eine XSLT-Transformation in einem XSLT-Stylesheet aus  
  
1.  Öffnen Sie ein XSLT-Stylesheet im XML-Editor.  
  
2.  Geben Sie eine XML-Dokument in der **Eingabe** Feld des Dokuments **Eigenschaften** Fenster.  
  
    > [!NOTE]
    >  Das XML-Dokument ist das für die Transformation verwendete Eingabedokument. Wenn ein Dokument nicht angegeben wird, wenn die XSLT-Transformation gestartet wird, die **Datei öffnen** Dialogfeld wird angezeigt, und Sie können ein Dokument zu diesem Zeitpunkt angeben.  
  
3.  Klicken Sie auf die **ShowXSLT Ausgabe** Schaltfläche der **XML-Editor** Symbolleiste.  
  
     Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.  
  
### <a name="to-provide-a-different-output-file-name"></a>So stellen Sie einen anderen Ausgabedateinamen bereit  
  
1.  Geben Sie einen Namen in der **Ausgabe** Feld des Dokuments **Eigenschaften** Fenster.  
  
2.  Klicken Sie auf die **ShowXSLT Ausgabe** Schaltfläche der **XML-Editor** Symbolleiste.  
  
     Die resultierende Ausgabe aus der XSLT-Transformation in einem neuen Dokumentfenster angezeigt wird, und im Ausgabefenster verwendete Editor hängt von der Erweiterungs der Ihre **Ausgabe** -Dokumenteigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor](../xml-tools/xml-editor.md)



