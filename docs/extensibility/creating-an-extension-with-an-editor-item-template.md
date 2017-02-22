---
title: "Erstellen eine Erweiterung mit einer Elementvorlage-Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] neue - Erweiterungen"
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen eine Erweiterung mit einer Elementvorlage-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Vorlagen verwenden, die Teil der Visual Studio SDK basic Editor\-Erweiterungen zu erstellen, die im Editor Klassifizierer, Details und Ränder hinzu. Die Editor\-Elementvorlagen sind für Visual c\# oder Visual Basic\-VSIX\-Projekte verfügbar.  
  
## Erforderliche Komponenten  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eine Classifier\-Erweiterung  
 Die Editor Classifier\-Elementvorlage erstellt eine Editor\-Klassifizierung, die den entsprechenden Text Farben \(in diesem Fall alles\) in eine Textdatei.  
  
1.  In der **Neues Projekt** Dialogfeld erweitern Sie **Visual C\#\-** oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** aus **VSIX\-Projekt**. In den **Namen** geben `TestClassifier`. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. Wechseln Sie zu Visual c\# **Erweiterbarkeit** Knoten, und wählen **Editor Klassifizierer**. Lassen Sie den Standardnamen \(EditorClassifier1.cs\).  
  
3.  Es gibt drei Codedateien wie folgt:  
  
    -   EditorClassifier1.cs enthält die `EditorClassifier1` Klasse.  
  
    -   EditorClassifier1ClassificationDefinition.cs enthält die `OEditorClassifier1ClassificationDefinition` Klasse.  
  
    -   EditorClassifier1Format.cs enthält die `EditorClassifier1Format`  Klasse.  
  
    -   EditorClassifier1Provider.cs enthält die `EditorClassifier1Provider` Klasse.  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
     Wenn Sie eine Textdatei öffnen, wird der gesamte Text mit einem violetten Hintergrund unterstrichen.  
  
## Erstellen einer relativen Text Adornment\-Erweiterung  
 Der Editor Text Adornment Vorlage erstellt einen Text relativ Adornment, die alle Instanzen des Textzeichens dekoriert "a" mit ein, die einen roten Konturen und ein blauer Hintergrund verfügt. Relative Text ist da das Feld immer überlagert das Zeichen 'a', selbst wenn sie verschoben oder neu formatiert werden.  
  
1.  In der **Neues Projekt** Dialogfeld erweitern Sie **Visual C\#\-** oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** aus **VSIX\-Projekt**. In den **Namen** geben `TestAdornment`. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. Wechseln Sie zu Visual c\# **Erweiterbarkeit** Knoten, und wählen **Editor Text Adornment**. Lassen Sie den Standardnamen \(TextAdornment1.cs\/vb\).  
  
3.  Es gibt zwei Codedateien:  
  
    -   TextAdornment1.cs enthält die `TextAdornment1` Klasse.  
  
    -   extAdornment1TextViewCreationListener.cs enthält die `TextAdornment1TextViewCreationListener` Klasse.  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird. Wenn Sie eine Textdatei öffnen, werden alle 'a' Zeichen im Text rot vor einem blauen Hintergrund beschrieben.  
  
## Erstellen einer Adornment Relative Viewport\-Erweiterung  
 Der Editor Viewport Randsteuerelement\-Vorlage erstellt eine Relative Viewport\-Adornment ein Violett hinzu, die einen roten Umriss zu der oberen rechten Ecke des Viewports hat.  
  
> [!NOTE]
>  Die *Viewport* ist der Bereich der Textansicht, die gerade angezeigt wird.  
  
#### Erweiterung Adornment Viewport mithilfe der Editor Viewport Randsteuerelement\-Vorlage erstellen  
  
1.  In der **Neues Projekt** Dialogfeld erweitern Sie **Visual C\#\-** oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** aus **VSIX\-Projekt**. In den **Namen** geben `ViewportAdornment`. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. Wechseln Sie zu Visual c\# **Erweiterbarkeit** Knoten, und wählen **Editor Viewport Adornment**. Lassen Sie den Standardnamen \(ViewportAdornment1.cs\/vb\).  
  
3.  Es gibt zwei Codedateien:  
  
    -   ViewportAdornment1.cs enthält die `ViewportAdornment1` Klasse.  
  
    -   ViewportAdornment1TextViewCreationListener.cs enthält die `ViewportAdornment1TextViewCreationListener` Klasse  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird. Wenn Sie eine neue Textdatei erstellen, wird ein Violett, die einen roten Umriss in der oberen rechten Ecke des Viewports angezeigt.  
  
## Erstellen einer Margin\-Erweiterung  
 Die Rand\-Editor\-Vorlage erstellt einen grünen Rand, der zusammen mit den Wörtern "Hello World\!" angezeigt wird. unterhalb der horizontalen Bildlaufleiste.  
  
#### Eine Rand\-Erweiterung mithilfe der Rand\-Editor\-Vorlage erstellen  
  
1.  In der **Neues Projekt** Dialogfeld erweitern Sie **Visual C\#\-** oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** aus **VSIX\-Projekt**. In den **Namen** geben `MarginExtension`. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. Wechseln Sie zu Visual c\# **Erweiterbarkeit** Knoten, und wählen **Editor Viewport Adornment**. Lassen Sie den Standardnamen \(EditorMargin1.cs\/vb\).  
  
3.  Es gibt zwei Codedateien:  
  
    -   EditorMargin1.cs enthält die `EditorMargin1` Klasse.  
  
    -   EditorMargin1Factory.cs enthält die `EditorMargin1Factory` Klasse.  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debuggen. Die experimentelle Instanz angezeigt wird. Wenn Sie eine Textdatei öffnen, wird ein grüner Rand, die die Wörter "Hello EditorMargin1" unter die horizontale Bildlaufleiste angezeigt.  
  
## Siehe auch  
 [Language Service und Erweiterungspunkte\-Editor](../extensibility/language-service-and-editor-extension-points.md)