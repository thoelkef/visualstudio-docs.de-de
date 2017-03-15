---
title: "Gewusst wie: Ausf&#252;hren einer XSLT-Transformation im XML-Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Gewusst wie: Ausf&#252;hren einer XSLT-Transformation im XML-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem XML\-Editor können Sie einem XML\-Dokument ein XSLT\-Stylesheet zuordnen, die Transformation ausführen und die Ausgabe anzeigen.Die aus der XSLT\-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.  
  
 Die **Output**\-Eigenschaft gibt den Dateinamen für die Ausgabe an.Wenn die **Output**\-Eigenschaft leer ist, wird der Dateiname in einem temporären Verzeichnis generiert.Die Dateierweiterung basiert auf dem `xsl:output`\-Element im Stylesheet and kann XML, TXT oder HTM sein.  
  
 Wenn in der **Output**\-Eigenschaft ein Dateiname mit einer HTM\- oder HTML\-Erweiterung angegeben ist, wird mit [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]\-Internet Explorer eine Vorschau auf die XSLT\-Ausgabe ermöglicht.Bei allen anderen Dateierweiterungen wird der von [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]\-Visual Studio ausgewählte Standard\-Editor verwendet.Bei Dateien mit der Erweiterung XML wird beispielsweise von Visual Studio der XML\-Editor verwendet.  
  
### So führen Sie eine XSLT\-Transformation in einem XML\-Dokument aus  
  
1.  Öffnen Sie ein XML\-Dokument im XML\-Editor.  
  
2.  Ordnen Sie dem XML\-Dokument ein XSLT\-Stylesheet zu.  
  
    -   Fügen Sie dem XML\-Dokument eine `xml-stylesheet`\-Verarbeitungsanweisung hinzu.Fügen Sie z. B. dem Dokumentprolog folgende Zeile `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` hinzu.  
  
         – oder –  
  
    -   Fügen Sie mithilfe des Eigenschaftenfensters das XSLT\-Stylesheet hinzu.Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Stylesheet** auf die Schaltfläche **Durchsuchen**, wählen Sie das XSLT\-Stylesheet aus, und klicken Sie auf **Öffnen**.  
  
3.  Klicken Sie auf der **XML\-Editor**\-Symbolleiste auf die Schaltfläche **XSLT\-Ausgabe anzeigen**.  
  
    > [!NOTE]
    >  Wenn dem XML\-Dokument kein Stylesheet zugeordnet ist, werden Sie in einem Dialogfeld aufgefordert, das zu verwendende Stylesheet bereitzustellen.  
    >   
    >  Die aus der XSLT\-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.  
  
### So führen Sie eine XSLT\-Transformation in einem XSLT\-Stylesheet aus  
  
1.  Öffnen Sie ein XSLT\-Stylesheet im XML\-Editor.  
  
2.  Geben Sie im Eigenschaftenfenster des Dokuments im Feld **Eingabe** ein XML\-Dokument an.  
  
    > [!NOTE]
    >  Das XML\-Dokument ist das für die Transformation verwendete Eingabedokument.Wenn beim Starten der XSLT\-Transformation kein Dokument angegeben wurde, wird das Dialogfeld **Datei öffnen** angezeigt, und Sie können nun ein Dokument angeben.  
  
3.  Klicken Sie auf der **XML\-Editor**\-Symbolleiste auf die Schaltfläche **XSLT\-Ausgabe anzeigen**.  
  
     Die aus der XSLT\-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.  
  
### So stellen Sie einen anderen Ausgabedateinamen bereit  
  
1.  Geben Sie im Eigenschaftenfenster des Dokuments im Feld **Ausgabe** einen Dateinamen an.  
  
2.  Klicken Sie auf der **XML\-Editor**\-Symbolleiste auf die Schaltfläche **XSLT\-Ausgabe anzeigen**.  
  
     Die resultierende Ausgabe aus der XSLT\-Transformation wird in einem neuen Dokumentfenster angezeigt. Der im Ausgabefenster verwendete Editor hängt von der Dateierweiterung der **Output**\-Dokumenteigenschaft ab.  
  
## Siehe auch  
 [XML\-Editor](../xml-tools/xml-editor.md)