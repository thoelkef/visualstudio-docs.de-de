---
title: 'Exemplarische Vorgehensweise: Anpassen der Textansicht | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697465"
---
# <a name="walkthrough-customize-the-text-view"></a>Exemplarische Vorgehensweise: Anpassen der Textansicht
Sie können eine Textansicht anpassen, indem Sie eine der folgenden Eigenschaften in der Editor-Format-Zuordnung ändern:

- Indikatorrand

- Einfügungspflege

- Pflege überschreiben

- Ausgewählter Text

- Inaktiver markierter Text (d. h. markierter Text, der den Fokus verloren hat)

- Sichtbarer Leerraum

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

1. Erstellen Sie ein Projekt von C-VSIX. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C/ Erweiterbarkeit**aus, dann **VSIX-Projekt**.) Benennen Sie `ViewPropertyTest`die Lösung .

2. Fügen Sie dem Projekt eine Editor-Klassifierelementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editorelementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="define-the-content-type"></a>Definieren des Inhaltstyps

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `ViewPropertyModifier`.

2. Fügen Sie die folgenden `using`-Anweisungen hinzu:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Deklarieren `TestViewCreationListener` Sie eine Klasse <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>mit dem Namen, die von erbt. Exportieren Sie diese Klasse mit den folgenden Attributen:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, um den Inhaltstyp anzugeben, auf den dieser Listener angewendet wird.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>, um die Rolle dieses Listeners anzugeben.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. Importieren Sie in <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>dieser Klasse die .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Ändern der Ansichtseigenschaften

1. Richten Sie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> die Methode so ein, dass die Ansichtseigenschaften beim Öffnen der Ansicht geändert werden. Um die Änderung vorzunehmen, <xref:System.Windows.ResourceDictionary> suchen Sie zuerst die, die dem Aspekt der Ansicht entspricht, die Sie suchen möchten. Ändern Sie dann die entsprechende Eigenschaft im Ressourcenwörterbuch, und legen Sie die Eigenschaften fest. Batch die Aufrufe <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> der Methode <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> durch Aufrufen der Methode, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> bevor Sie die Eigenschaften und dann die nachdem Sie die Eigenschaften festlegen.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes

1. Erstellen Sie die Projektmappe.

     Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

2. Erstellen Sie eine Textdatei, und geben Sie Text ein.

    - Die Einfügepflege sollte magenta und die überschreibende Pflege türkis sein.

    - Der Indikatorrand (links in der Textansicht) sollte hellgrün sein.

3. Wählen Sie den eingegebenen Text aus. Die Farbe des markierten Textes sollte hellrosa sein.

4. Wenn der Text ausgewählt ist, klicken Sie auf eine beliebige Stelle außerhalb des Textfensters. Die Farbe des markierten Textes sollte dunkelrosa sein.

5. Aktivieren Sie den sichtbaren Leerraum. (Zeigen Sie im Menü **Bearbeiten** auf **Erweitert,** und klicken Sie dann auf **Leerraum anzeigen**). Geben Sie einige Registerkarten in den Text ein. Rote Pfeile, die die Registerkarten darstellen, sollten angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)
