---
title: 'Exemplarische Vorgehensweise: Anpassen der Textansicht | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ecbf5e3bed5ba506278f00b2b5b0b76f8f02850a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-customizing-the-text-view"></a>Exemplarische Vorgehensweise: Anpassen der Textansicht
Sie können eine Textansicht anpassen, indem Sie ändern die folgenden Eigenschaften in der Map-Editor-Format:  
  
-   Indikatorrand  
  
-   Einfügemarke  
  
-   Überschreiben Sie die Einfügemarke  
  
-   Ausgewählten text  
  
-   Inaktiver ausgewählter Text (d. h. markierten Text, den Fokus verliert)  
  
-   Sichtbare Leerstellen  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekts**.) Nennen Sie die Projektmappe `ViewPropertyTest`.  
  
2.  Dem Projekt eine Elementvorlage Editor Klassifizierer hinzugefügt. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einer Elementvorlage Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="defining-the-content-type"></a>Definieren den Inhaltstyp  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `ViewPropertyModifier`.  
  
2.  Fügen Sie die folgenden `using` Direktiven:  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Deklarieren Sie eine Klasse mit dem Namen `TestViewCreationListener` von erbt <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exportieren Sie diese Klasse mit den folgenden Attributen:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>den Typ des Inhalts angeben, dieses Listeners gilt.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>um die Rolle dieses Listeners anzugeben.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  In dieser Klasse importiert die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Ändern die Eigenschaften anzeigen  
  
1.  Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, damit die Eigenschaften der Ansicht geändert werden, wenn die Ansicht geöffnet wird. Um die Änderung vorzunehmen, suchen Sie zuerst die <xref:System.Windows.ResourceDictionary> , entspricht der Aspekt der Sicht, die Sie suchen möchten. Klicken Sie dann die entsprechende Eigenschaft im Ressourcenverzeichnis ändern und Festlegen der Eigenschaften. Batchverarbeitung der Aufrufe an die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> Methode durch Aufrufen der <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> -Methode auf, bevor Sie die Eigenschaften festlegen und dann die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> nach dem Festlegen der Eigenschaften.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
  
1.  Erstellen Sie die Projektmappe.  
  
     Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
2.  Erstellen Sie eine Textdatei, und geben Sie Text ein.  
  
    -   Die Einfügemarke sollte Magenta und das Caretzeichen überschreiben Türkis werden sollte.  
  
    -   Indikatorrand (auf der linken Seite der Textansicht) muss Licht grün.  
  
3.  Wählen Sie den Text, den Sie gerade eingegeben haben. Die Farbe des markierten Texts muss Licht rosa.  
  
4.  Während der Text ausgewählt ist, klicken Sie auf eine beliebige Stelle außerhalb des Textfensters. Die Farbe des markierten Texts sollte dunkel Folgendes ein: rosa.  
  
5.  Aktivieren Sie sichtbare Leerstellen. (Auf der **bearbeiten** Sie im Menü **erweitert** , und klicken Sie dann auf **Leerstelle anzeigen**). Geben Sie einige Registerkarten in den Text ein. Rote Pfeile, die darstellen, die Registerkarten angezeigt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)