---
title: "Exemplarische Vorgehensweise: Anpassen der Textansicht | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] neu – Anpassen der Ansicht"
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Exemplarische Vorgehensweise: Anpassen der Textansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine Textansicht anpassen, ändern Sie die folgenden Eigenschaften in der Map\-Editor\-Format:  
  
-   Indikatorrand  
  
-   Einfügemarke  
  
-   Überschreiben Sie die Einfügemarke  
  
-   Ausgewählten text  
  
-   Inaktiver ausgewählter Text \(d. h. markierten Text, den Fokus verliert\)  
  
-   Sichtbare Leerstellen  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise ausführen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Erstellen eines MEF\-Projekts  
  
1.  Erstellen Sie ein C\#\-VSIX\-Projekt. \(In der **Neues Projekt** Dialogfeld **Visual c\# \/ Erweiterbarkeit**, dann **VSIX\-Projekt**.\) Nennen Sie die Projektmappe `ViewPropertyTest`.  
  
2.  Fügen Sie dem Projekt eine Classifier\-Editor\-Elementvorlage hinzu. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einer Elementvorlage\-Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandene Klassendateien.  
  
## Den Inhaltstyp definieren  
  
1.  Fügen Sie eine Klassendatei hinzu, und nennen Sie es `ViewPropertyModifier`.  
  
2.  Fügen Sie die folgenden `using` Direktiven:  
  
     [!code-cs[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Deklarieren Sie eine Klasse mit dem Namen `TestViewCreationListener` die von erbt <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exportieren Sie diese Klasse mit den folgenden Attributen:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> den Typ des Inhalts angeben, für den Listener gilt.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> um die Rolle dieses Listeners anzugeben.  
  
     [!code-cs[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  Importieren Sie in dieser Klasse die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!code-cs[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## Ändern die Eigenschaften anzeigen  
  
1.  Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, damit die Eigenschaften geändert werden, wenn die Ansicht geöffnet wird. Um die Änderung vorzunehmen, suchen Sie zuerst die <xref:System.Windows.ResourceDictionary> entspricht der Aspekt der Ansicht, die Sie suchen möchten. Ändern Sie die entsprechende Eigenschaft im Ressourcenverzeichnis, und legen Sie die Eigenschaften. Batch die Aufrufe an die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> Methode durch Aufrufen der <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> \-Methode auf, bevor Sie die Eigenschaften festlegen und dann die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> nach dem Festlegen der Eigenschaften.  
  
     [!code-cs[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## Erstellen und Testen des Codes  
  
1.  Erstellen Sie die Projektmappe.  
  
     Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
2.  Erstellen Sie eine Textdatei, und geben Sie Text ein.  
  
    -   Die Einfügemarke sollten Magenta und die Einfügemarke überschreiben Türkis sein sollte.  
  
    -   Indikatorrand \(auf der linken Seite der Textansicht\) sollte Licht grün.  
  
3.  Wählen Sie den Text, den Sie gerade eingegeben. Die Farbe des ausgewählten Texts sollte Licht rosa.  
  
4.  Während der Text ausgewählt ist, klicken Sie auf eine beliebige Stelle außerhalb des Textfensters. Die Farbe des ausgewählten Texts sollte dunkel Pink.  
  
5.  Aktivieren Sie sichtbare Leerstellen. \(Auf der **Bearbeiten** auf **Erweitert** und klicken Sie dann auf **Leerstelle anzeigen**\). Geben Sie einige Registerkarten im Text. Rote Pfeile, die darstellen, die Registerkarten angezeigt werden sollen.  
  
## Siehe auch  
 [Language Service und Erweiterungspunkte\-Editor](../extensibility/language-service-and-editor-extension-points.md)