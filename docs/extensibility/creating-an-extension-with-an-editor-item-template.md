---
title: Erstellen eine Erweiterung mit einer Elementvorlage-Editor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fb66dfffaf8fa8339ce9060c912dc358fb454a7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Erstellen eine Erweiterung mit einer Elementvorlage-Editor
Sie können Vorlagen verwenden, die enthalten sind, im Visual Studio SDK grundlegender Editor-Erweiterungen erstellen, die im Editor Klassifizierern Zusatzelemente und Ränder hinzu. Der Editor Elementvorlagen sind für Visual c# oder Visual Basic-VSIX-Projekte verfügbar.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Erstellen einer Klassifizierung-Erweiterung  
 Die Editor Klassifizierer Elementvorlage erstellt eine Editor-Klassifizierung, die den entsprechenden Text Farben (in diesem Fall alles) in eine Textdatei.  
  
1.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic** , und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** klicken Sie im Bereich **VSIX-Projekt**. Geben Sie im Feld **Name** `TestClassifier`ein. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. Wechseln Sie zu Visual c# **Erweiterbarkeit** Knoten, und wählen **Editor Klassifizierer**. Lassen Sie den Standarddateinamen (EditorClassifier1.cs).  
  
3.  Es gibt drei Codedateien, wie folgt:  
  
    -   EditorClassifier1.cs enthält die `EditorClassifier1` Klasse.  
  
    -   EditorClassifier1ClassificationDefinition.cs enthält die `OEditorClassifier1ClassificationDefinition` Klasse.  
  
    -   EditorClassifier1Format.cs enthält die `EditorClassifier1Format` Klasse.  
  
    -   EditorClassifier1Provider.cs enthält die `EditorClassifier1Provider` Klasse.  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
     Wenn Sie eine Textdatei öffnen, wird der gesamte Text vor einem Hintergrund violett unterstrichen.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Erstellen einer Text-Relative Randsteuerelement-Erweiterung  
 Der Editor Text Randsteuerelement-Vorlage erstellt einen Text-Relative Zusatzelement (adornment), die alle Instanzen des Textzeichens ergänzt "a" mithilfe eines Felds, das eine rote Gliederung und einen blauen Hintergrund verfügt. Es ist relativ zum Text da Feld immer überlagert "a" die Zeichen, selbst wenn sie verschoben oder neu formatiert werden.  
  
1.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic** , und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** klicken Sie im Bereich **VSIX-Projekt**. Geben Sie im Feld **Name** `TestAdornment`ein. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. Wechseln Sie zu Visual c# **Erweiterbarkeit** Knoten, und wählen **Editor Text Randsteuerelement**. Lassen Sie den Standarddateinamen (TextAdornment1.cs/vb).  
  
3.  Es gibt zwei Codedateien wie folgt:  
  
    -   TextAdornment1.cs enthält die `TextAdornment1` Klasse.  
  
    -   extAdornment1TextViewCreationListener.cs enthält die `TextAdornment1TextViewCreationListener` Klasse.  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird. Wenn Sie eine Textdatei öffnen, werden die "a" Zeichen im Text rot vor einem blauen Hintergrund beschrieben.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Erstellen einer relativ zum Viewport Randsteuerelement-Erweiterung  
 Die Editor Viewport Randsteuerelement-Vorlage erstellt eine Relative Viewport Randsteuerelement eine violette Feld hinzu, die einen roten Umriss zu der oberen rechten Ecke des Viewports hat.  
  
> [!NOTE]
>  Die *Viewport* ist der Bereich der Textansicht, die derzeit angezeigt wird.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>So erstellen eine Viewport Randsteuerelement-Erweiterung mithilfe der Editor Viewport Randsteuerelement-Vorlage  
  
1.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic** , und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** klicken Sie im Bereich **VSIX-Projekt**. Geben Sie im Feld **Name** `ViewportAdornment`ein. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. Wechseln Sie zu Visual c# **Erweiterbarkeit** Knoten, und wählen **Editor Viewport Randsteuerelement**. Lassen Sie den Standarddateinamen (ViewportAdornment1.cs/vb).  
  
3.  Es gibt zwei Codedateien wie folgt:  
  
    -   ViewportAdornment1.cs enthält die `ViewportAdornment1` Klasse.  
  
    -   ViewportAdornment1TextViewCreationListener.cs enthält die `ViewportAdornment1TextViewCreationListener` Klasse  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird. Wenn Sie eine neue Textdatei erstellen, wird eine violette Box, die einen roten Umriss wurde in der oberen rechten Ecke des Viewports angezeigt.  
  
## <a name="creating-a-margin-extension"></a>Erstellen einer Margin-Erweiterung  
 Die Rand-Editor-Vorlage erstellt einen grünen Rand, der zusammen mit den Wörtern "Hello World!" angezeigt wird. unterhalb der horizontalen Bildlaufleiste.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>So erstellen eine Erweiterungs-Rand mithilfe der Rand-Editor-Vorlage  
  
1.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic** , und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** klicken Sie im Bereich **VSIX-Projekt**. Geben Sie im Feld **Name** `MarginExtension`ein. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. Wechseln Sie zu Visual c# **Erweiterbarkeit** Knoten, und wählen **Editor Viewport Randsteuerelement**. Lassen Sie den Standarddateinamen (EditorMargin1.cs/vb).  
  
3.  Es gibt zwei Codedateien wie folgt:  
  
    -   EditorMargin1.cs enthält die `EditorMargin1` Klasse.  
  
    -   EditorMargin1Factory.cs enthält die `EditorMargin1Factory` Klasse.  
  
4.  Dieses Projekt zu erstellen und mit dem Debuggen beginnen. Die experimentelle Instanz angezeigt wird. Wenn Sie eine Textdatei öffnen, wird ein grüner Rand, die die Wörter "Hello EditorMargin1" unter die horizontale Bildlaufleiste angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)