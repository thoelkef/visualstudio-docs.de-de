---
title: Erstellen einer Erweiterung mit einer Editor-Elementvorlage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 245963c433c264212096d129d99d86367e006b4f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513110"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Erstellen einer Erweiterung mit einer Editor-Elementvorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](https://docs.microsoft.com/visualstudio/extensibility/creating-an-extension-with-an-editor-item-template).  
  
Sie können Vorlagen verwenden, die enthalten sind, im Visual Studio SDK einfachen Editor-Erweiterungen zu erstellen, die Klassifizierungen, Zusatzelemente und Ränder im Editor hinzu. Die Editor-Elementvorlagen sind für Visual c# oder Visual Basic-VSIX-Projekte verfügbar.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Erstellen einer Klassifizierungsfunktion-Erweiterung  
 Die Editor-Klassifizierer Item-Vorlage erstellt eine Editor-Klassifizierung, die den entsprechenden Text Farben (in diesem Fall alle) in eine Textdatei.  
  
1.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic** , und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** wählen Sie im Bereich **VSIX-Projekt**. Geben Sie im Feld **Name** `TestClassifier`ein. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. Wechseln Sie in der Visual c# **Erweiterbarkeit** Knoten, und wählen **Editor Klassifizierer**. Lassen Sie den Standarddateinamen (EditorClassifier1.cs) aus.  
  
3.  Es gibt drei Codedateien, wie folgt:  
  
    -   EditorClassifier1.cs enthält die `EditorClassifier1` Klasse.  
  
    -   EditorClassifier1ClassificationDefinition.cs enthält die `OEditorClassifier1ClassificationDefinition` Klasse.  
  
    -   EditorClassifier1Format.cs enthält die `EditorClassifier1Format` Klasse.  
  
    -   EditorClassifier1Provider.cs enthält die `EditorClassifier1Provider` Klasse.  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
     Wenn Sie eine Textdatei öffnen, wird der gesamte Text mit einem violetten Hintergrund unterstrichen.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Erstellen einer relativen Text Zusatzelement-Erweiterung  
 Der Editor Text Zusatzelement-Vorlage erstellt einen Text relativ Zusatzelement, das alle Instanzen des Textzeichens dekoriert "a" mit der ein Feld, das ein roter Rahmen und einem blauen Hintergrund hat. Es ist relativ Text da das Feld immer überlagert die Zeichen 'a', auch wenn sie verschoben oder neu formatiert werden.  
  
1.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic** , und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** wählen Sie im Bereich **VSIX-Projekt**. Geben Sie im Feld **Name** `TestAdornment`ein. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. Wechseln Sie in der Visual c# **Erweiterbarkeit** Knoten, und wählen **Editor Text Zusatzelement**. Lassen Sie den Standarddateinamen (TextAdornment1.cs/vb) aus.  
  
3.  Es gibt zwei Codedateien, wie folgt:  
  
    -   TextAdornment1.cs enthält die `TextAdornment1` Klasse.  
  
    -   extAdornment1TextViewCreationListener.cs enthält die `TextAdornment1TextViewCreationListener` Klasse.  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird. Wenn Sie eine Textdatei öffnen, werden alle "a"-Zeichen in den Text in Rot mit einem blauen Hintergrund beschrieben.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Erstellen einer Relative Viewport-Zusatzelement-Erweiterung  
 Die Editor Viewport Zusatzelement-Vorlage erstellt eine Relative Viewport-Zusatzelement eine violette Feld hinzu, die einen roten Rahmen auf der oberen rechten Ecke des Viewports hat.  
  
> [!NOTE]
>  Die *Viewport* ist der Bereich der Textansicht, die derzeit angezeigt wird.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Eine Erweiterung des Viewports Zusatzelement mithilfe der Editor Viewport Zusatzelement-Vorlage erstellen  
  
1.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic** , und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** wählen Sie im Bereich **VSIX-Projekt**. Geben Sie im Feld **Name** `ViewportAdornment`ein. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. Wechseln Sie in der Visual c# **Erweiterbarkeit** Knoten, und wählen **Editor Viewport Zusatzelement**. Lassen Sie den Standarddateinamen (ViewportAdornment1.cs/vb) aus.  
  
3.  Es gibt zwei Codedateien, wie folgt:  
  
    -   ViewportAdornment1.cs enthält die `ViewportAdornment1` Klasse.  
  
    -   ViewportAdornment1TextViewCreationListener.cs enthält die `ViewportAdornment1TextViewCreationListener` Klasse  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird. Wenn Sie eine neue Textdatei erstellen, wird ein Violett, die einen roten Rahmen hat das in der oberen rechten Ecke des Viewports angezeigt.  
  
## <a name="creating-a-margin-extension"></a>Erstellen einer Margin-Erweiterung  
 Die Rand des Editors-Vorlage erstellt einen grünen Rand, der zusammen mit den Wörtern "Hello World!" angezeigt wird. Klicken Sie unten die horizontale Bildlaufleiste.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>So erstellen Sie eine Margin-Erweiterung mithilfe der Vorlage Rand des Editors  
  
1.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic** , und klicken Sie dann auf **Erweiterbarkeit**. In der **Vorlagen** wählen Sie im Bereich **VSIX-Projekt**. Geben Sie im Feld **Name** `MarginExtension`ein. Klicken Sie auf **OK**.  
  
2.  In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. Wechseln Sie in der Visual c# **Erweiterbarkeit** Knoten, und wählen **Editor Viewport Zusatzelement**. Lassen Sie den Standarddateinamen (EditorMargin1.cs/vb) aus.  
  
3.  Es gibt zwei Codedateien, wie folgt:  
  
    -   EditorMargin1.cs enthält die `EditorMargin1` Klasse.  
  
    -   EditorMargin1Factory.cs enthält die `EditorMargin1Factory` Klasse.  
  
4.  Dieses Projekt erstellen und mit dem Debuggen beginnen. Die experimentelle Instanz angezeigt wird. Wenn Sie eine Textdatei öffnen, wird ein grüner Rand, die die Wörter "Hello EditorMargin1" unter die horizontale Bildlaufleiste angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)

