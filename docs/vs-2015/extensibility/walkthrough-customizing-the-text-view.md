---
title: 'Exemplarische Vorgehensweise: Anpassen der Textansicht | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38cbd0117f5f49666ee5da42d0f60dadf451ffda
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781815"
---
# <a name="walkthrough-customizing-the-text-view"></a>Exemplarische Vorgehensweise: Anpassen der Textansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Textansicht anpassen, indem Sie die folgenden Eigenschaften in der Map-Editor-Format ändern:  
  
-   Indikatorrand  
  
-   Einfügen, Einfügemarke  
  
-   Überschreiben Sie die Einfügemarke  
  
-   Ausgewählten text  
  
-   Inaktiver ausgewählter Text (d. h. ausgewählten Text, der Fokus verloren hat)  
  
-   Sichtbare Leerstellen  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
1.  Erstellen Sie ein C#-VSIX-Projekt. (In der **neues Projekt** wählen Sie im Dialogfeld **Visual c# / Erweiterbarkeit**, klicken Sie dann **VSIX-Projekt**.) Nennen Sie die Projektmappe `ViewPropertyTest`.  
  
2.  Fügen Sie eine Elementvorlage Editor Klassifizierer zum Projekt hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="defining-the-content-type"></a>Definieren den Inhaltstyp  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `ViewPropertyModifier`.  
  
2. Fügen Sie die folgenden `using` Anweisungen:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Deklarieren Sie eine Klasse, die mit dem Namen `TestViewCreationListener` von erbt <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Exportieren Sie diese Klasse mit den folgenden Attributen:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> den Typ des Inhalts angeben, für die dieser Listener gilt.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> um die Rolle dieses Listeners anzugeben.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. In dieser Klasse importiert die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Ändern der Eigenschaften anzeigen  
  
1.  Implementieren der <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, damit die Eigenschaften der Ansicht geändert werden, wenn die Ansicht geöffnet wird. Um die Änderung vorzunehmen, suchen Sie zuerst die <xref:System.Windows.ResourceDictionary> , entspricht der Aspekt der Ansicht gesucht werden soll. Klicken Sie dann ändern Sie die entsprechende Eigenschaft im Ressourcenverzeichnis aus, und legen Sie die Eigenschaften. Batch die Aufrufe an die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> -Methode durch Aufrufen der <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> -Methode auf, bevor Sie die Eigenschaften festlegen und dann die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> nach dem Festlegen der Eigenschaften.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
  
1.  Erstellen Sie die Projektmappe.  
  
     Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
2.  Erstellen Sie eine Textdatei, und geben Sie Text ein.  
  
    -   Die Einfügemarke einfügen sollten Magenta und die Einfügemarke überschreiben muss Türkis.  
  
    -   Indikatorrand (auf der linken Seite der Textansicht) muss ein Licht grün.  
  
3.  Wählen Sie den gerade eingegebenen Text. Die Farbe des ausgewählten Texts muss Licht rosa.  
  
4.  Während der Text ausgewählt ist, klicken Sie auf eine beliebige Stelle außerhalb des Textfensters. Die Farbe des ausgewählten Texts sollte dunkel Folgendes ein: rosa.  
  
5.  Aktivieren Sie sichtbarer Leerraum. (Auf der **bearbeiten** Startmenü **erweitert** , und klicken Sie dann auf **Leerstelle anzeigen**). Geben Sie einige Registerkarten in den Text ein. Rote Pfeile, die darstellen, die Registerkarten angezeigt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)

