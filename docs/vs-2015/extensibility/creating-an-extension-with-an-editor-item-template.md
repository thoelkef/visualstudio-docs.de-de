---
title: Erstellen einer Erweiterung mit einer Editor-Element Vorlage | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ccdd87d44ee90c925992f4d7b997c9bbe09684
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841296"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Erstellen einer Erweiterung mit einer Editor-Elementvorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von Element Vorlagen, die im Visual Studio SDK enthalten sind, können Sie grundlegende Editor-Erweiterungen erstellen, mit denen Klassifizierer, Zusatzelemente und Ränder zum Editor hinzugefügt werden. Die Editor-Element Vorlagen sind für Visual c#-oder Visual Basic VSIX-Projekte verfügbar.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Erstellen einer Klassifizierungs Erweiterung  
 Die Element Vorlage für den Editor-Klassifizierer erstellt einen editorklassifizierer, der den entsprechenden Text (in diesem Fall alles) in einer beliebigen Textdatei färbt.  
  
1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#** , oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** die Option **VSIX-Projekt**aus. Geben Sie im Feld **Name**`TestClassifier`ein. Klicken Sie auf **OK**.  
  
2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus. Wechseln Sie zum Visual c#- **Erweiterbarkeits** Knoten, und wählen Sie **Editor Klassifizierer**aus. Belassen Sie den Standard Dateinamen (EditorClassifier1.cs).  
  
3. Es gibt drei Code Dateien, wie im folgenden dargestellt:  
  
    - EditorClassifier1.cs enthält die- `EditorClassifier1` Klasse.  
  
    - EditorClassifier1ClassificationDefinition.cs enthält die- `OEditorClassifier1ClassificationDefinition` Klasse.  
  
    - EditorClassifier1Format.cs enthält die- `EditorClassifier1Format`  Klasse.  
  
    - EditorClassifier1Provider.cs enthält die- `EditorClassifier1Provider` Klasse.  
  
4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
     Wenn Sie eine Textdatei öffnen, wird der gesamte Text gegen einen violetten Hintergrund unterstrichen.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Erstellen einer Erweiterung für Text-relative Zusatzelemente  
 Mit der Editor-Text Zusatz Vorlage wird ein Text relativer Zusatzelement erstellt, das alle Instanzen des Text Zeichens "a" mit einem Feld mit einer roten Kontur und einem blauen Hintergrund ergänzt. Er ist Text relativ, da das Feld immer die Zeichen "a" überlagert, auch wenn Sie verschoben oder neu formatiert werden.  
  
1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#** , oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** die Option **VSIX-Projekt**aus. Geben Sie im Feld **Name**`TestAdornment`ein. Klicken Sie auf **OK**.  
  
2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus. Wechseln Sie zum Visual c#- **Erweiterbarkeits** Knoten, und wählen Sie **Editor-Text**Zusatzelement aus. Belassen Sie den Standard Dateinamen (TextAdornment1.cs/VB).  
  
3. Es gibt zwei Code Dateien, wie im folgenden dargestellt:  
  
    - TextAdornment1.cs enthält die- `TextAdornment1` Klasse.  
  
    - extAdornment1TextViewCreationListener.cs enthält die- `TextAdornment1TextViewCreationListener` Klasse.  
  
4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet. Wenn Sie eine Textdatei öffnen, werden alle "a"-Zeichen im Text rot vor einem blauen Hintergrund dargestellt.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Erstellen einer Erweiterung für Viewport-relative Zusatzelemente  
 Mit der-Editor-Zusatzelement Vorlage wird ein Viewport-relativer Zusatzelement erstellt, das ein violettfeld mit einer roten Kontur in der oberen rechten Ecke des Viewports hinzufügt.  
  
> [!NOTE]
> Der *Viewport* ist der Bereich der aktuell angezeigten Textansicht.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>So erstellen Sie eine Viewport-Zusatzelement-Erweiterung mithilfe der Editor-Zusatzelement Vorlage  
  
1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#** , oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** die Option **VSIX-Projekt**aus. Geben Sie im Feld **Name**`ViewportAdornment`ein. Klicken Sie auf **OK**.  
  
2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus. Wechseln Sie zum Visual c#- **Erweiterbarkeits** Knoten, und wählen Sie **Editor Viewport**-Zusatzelement aus. Belassen Sie den Standard Dateinamen (ViewportAdornment1.cs/VB).  
  
3. Es gibt zwei Code Dateien, wie im folgenden dargestellt:  
  
    - ViewportAdornment1.cs enthält die- `ViewportAdornment1` Klasse.  
  
    - ViewportAdornment1TextViewCreationListener.cs enthält die- `ViewportAdornment1TextViewCreationListener` Klasse.  
  
4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet. Wenn Sie eine neue Textdatei erstellen, wird in der oberen rechten Ecke des Viewports ein violettfeld mit einem roten Umriss angezeigt.  
  
## <a name="creating-a-margin-extension"></a>Erstellen einer Rand Erweiterung  
 Die Vorlage für den Editor Rand erstellt einen grünen Rand, der mit den Wörtern "Hello World!" angezeigt wird. unterhalb der horizontalen Scrollleiste.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>So erstellen Sie eine Rand Erweiterung mithilfe der Editor-Rand Vorlage  
  
1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **Visual c#** , oder **Visual Basic** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** die Option **VSIX-Projekt**aus. Geben Sie im Feld **Name**`MarginExtension`ein. Klicken Sie auf **OK**.  
  
2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus. Wechseln Sie zum Visual c#- **Erweiterbarkeits** Knoten, und wählen Sie **Editor Viewport**-Zusatzelement aus. Belassen Sie den Standard Dateinamen (EditorMargin1.cs/VB).  
  
3. Es gibt zwei Code Dateien, wie im folgenden dargestellt:  
  
    - EditorMargin1.cs enthält die- `EditorMargin1` Klasse.  
  
    - EditorMargin1Factory.cs enthält die- `EditorMargin1Factory` Klasse.  
  
4. Erstellen Sie dieses Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet. Wenn Sie eine Textdatei öffnen, wird unterhalb der horizontalen Scrollleiste ein grüner Rand mit den Wörtern "Hello EditorMargin1" angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)
