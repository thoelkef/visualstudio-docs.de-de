---
title: Erstellen einer Erweiterung mit einer Editorelementvorlage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739505"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Erstellen einer Erweiterung mit einer Editorelementvorlage
Sie können Elementvorlagen verwenden, die im Visual Studio SDK enthalten sind, um grundlegende Editorerweiterungen zu erstellen, die dem Editor Klassifikatoren, Verzierungen und Ränder hinzufügen. Die Editorelementvorlagen sind für Visual C- oder Visual Basic VSIX-Projekte verfügbar.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Erstellen einer Klassifiererweiterung
 Die Editor-Klassifierelementvorlage erstellt einen Editorklassifier, der den entsprechenden Text (in diesem Fall alles) in einer beliebigen Textdatei färbt.

1. Erweitern Sie im Dialogfeld **Neues Projekt** Visual **C oder** Visual **Basic,** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** **VSIX Project**aus. Geben Sie im Feld **Name** die Zeichenfolge `TestClassifier` ein. Klicken Sie auf **OK**.

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie zum Knoten "Visual **C-Extensibility",** und wählen Sie **Editor-Klassifizierer**aus. Lassen Sie den Standarddateinamen (*EditorClassifier1.cs*).

3. Es gibt vier Codedateien, wie folgt:

    - *EditorClassifier1.cs* enthält `EditorClassifier1` die Klasse.

    - *EditorClassifier1ClassificationDefinition.cs* enthält `EditorClassifier1ClassificationDefinition` die Klasse.

    - *EditorClassifier1Format.cs* enthält `EditorClassifier1Format` die Klasse.

    - *EditorClassifier1Provider.cs* enthält `EditorClassifier1Provider` die Klasse.

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.

     Wenn Sie eine Textdatei öffnen, wird der gesamte Text vor einem violetten Hintergrund unterstrichen.

## <a name="create-a-text-relative-adornment-extension"></a>Erstellen einer textrelativen Verzierungserweiterung
 Die Vorlage "Editor Text Adornment" erstellt eine textrelative Verzierung, die alle Instanzen des Textzeichens "a" mit einem Feld mit roter Umriss und blauem Hintergrund schmückt. Sie ist textrelativ, da das Feld die "a"-Zeichen immer überlagert, auch wenn sie verschoben oder neu formatiert werden.

1. Erweitern Sie im Dialogfeld **Neues Projekt** Visual **C oder** Visual **Basic,** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** **VSIX Project**aus. Geben Sie im Feld **Name** die Zeichenfolge `TestAdornment` ein. Klicken Sie auf **OK**.

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie zum Knoten "Visual **C-Extensibility",** und wählen Sie **Editor Text Adornment**aus. Lassen Sie den Standarddateinamen (*TextAdornment1.cs/vb*).

3. Es gibt zwei Codedateien, wie folgt:

    - *TextAdornment1.cs* enthält `TextAdornment1` die Klasse.

    - *TextAdornment1TextViewCreationListener.cs* enthält `TextAdornment1TextViewCreationListener` die Klasse.

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt. Wenn Sie eine Textdatei öffnen, werden alle A-Zeichen im Text rot vor einem blauen Hintergrund umrandet.

## <a name="create-a-viewport-relative-adornment-extension"></a>Erstellen einer Ansichtsfenster-relativen Verzierungserweiterung
 Die Vorlage "Editor Viewport Adornment" erstellt eine Ansichtsfenster-relative Verzierung, die ein violettes Feld mit einer roten Umrisslinie zur oberen rechten Ecke des Ansichtsfensters hinzufügt.

> [!NOTE]
> Das **Ansichtsfenster** ist der Bereich der Textansicht, der derzeit angezeigt wird.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>So erstellen Sie eine Ansichtsfenster-Verzierungserweiterung mithilfe der Vorlage "Editor Viewport Adornment"

1. Erweitern Sie im Dialogfeld **Neues Projekt** Visual **C oder** Visual **Basic,** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** **VSIX Project**aus. Geben Sie im Feld **Name** die Zeichenfolge `ViewportAdornment` ein. Klicken Sie auf **OK**.

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie zum Knoten "Visual **C-Extensibility",** und wählen Sie **Editor Viewport Adornment**aus. Lassen Sie den Standarddateinamen (*ViewportAdornment1.cs/vb*).

3. Es gibt zwei Codedateien, wie folgt:

    - *ViewportAdornment1.cs* enthält `ViewportAdornment1` die Klasse.

    - *ViewportAdornment1TextViewCreationListener.cs* enthält `ViewportAdornment1TextViewCreationListener` die Klasse

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt. Wenn Sie eine neue Textdatei erstellen, wird in der oberen rechten Ecke des Ansichtsfensters ein violettes Feld mit einer roten Umrisslinie angezeigt.

## <a name="create-a-margin-extension"></a>Erstellen einer Margin-Erweiterung
 Die Editor Margin-Vorlage erstellt einen grünen Rand, der zusammen mit den Wörtern **Hallo Welt!* unterhalb der horizontalen Bildlaufleiste.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>So erstellen Sie eine Margin-Erweiterung mithilfe der Editor-Margin-Vorlage

1. Erweitern Sie im Dialogfeld **Neues Projekt** Visual **C oder** Visual **Basic,** und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie im Bereich **Vorlagen** **VSIX Project**aus. Geben Sie im Feld **Name** die Zeichenfolge `MarginExtension` ein. Klicken Sie auf **OK**.

2. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie zum Knoten "Visual **C-Extensibility",** und wählen Sie **Editor Margin aus.** Lassen Sie den Standarddateinamen (EditorMargin1.cs/vb).

3. Es gibt zwei Codedateien, wie folgt:

    - *EditorMargin1.cs* enthält `EditorMargin1` die Klasse.

    - *EditorMargin1Factory.cs* enthält `EditorMargin1Factory` die Klasse.

4. Erstellen Sie dieses Projekt, und beginnen Sie mit dem Debuggen. Die experimentelle Instanz wird angezeigt. Wenn Sie eine Textdatei öffnen, wird unterhalb der horizontalen Bildlaufleiste ein grüner Rand mit den Worten **Hello EditorMargin1** angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
