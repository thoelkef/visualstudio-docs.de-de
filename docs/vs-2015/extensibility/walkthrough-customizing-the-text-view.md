---
title: 'Exemplarische Vorgehensweise: Anpassen der Text Ansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202021"
---
# <a name="walkthrough-customizing-the-text-view"></a>Exemplarische Vorgehensweise: Anpassen der Textansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Textansicht anpassen, indem Sie die folgenden Eigenschaften in der Editor-Format-Karte ändern:  
  
- Indikatorrand  
  
- Einfügemarke  
  
- Caretzeichen überschreiben  
  
- Ausgewählter Text  
  
- Inaktiver ausgewählter Text (d. h. ausgewählter Text, der den Fokus verliert)  
  
- Sichtbare Leerräume  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Erstellen eines MEF-Projekts  
  
1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit**und dann **VSIX-Projekt**aus.) Benennen Sie die Projekt Mappe `ViewPropertyTest` .  
  
2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Löschen Sie die vorhandenen Klassendateien.  
  
## <a name="defining-the-content-type"></a>Definieren des Inhaltstyps  
  
1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `ViewPropertyModifier`.  
  
2. Fügen Sie die folgenden `using`-Anweisungen hinzu:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Deklarieren Sie eine Klasse mit dem Namen `TestViewCreationListener` , die von erbt <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Exportieren Sie diese Klasse mit den folgenden Attributen:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , um den Inhaltstyp anzugeben, für den dieser Listener gilt.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> zum Angeben der Rolle dieses Listener.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. Importieren Sie in dieser Klasse <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Ändern der Ansichts Eigenschaften  
  
1. Implementieren Sie die- <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Methode, sodass die Ansichts Eigenschaften beim Öffnen der Ansicht geändert werden. Um die Änderung vorzunehmen, suchen Sie zuerst <xref:System.Windows.ResourceDictionary> nach der, die dem Aspekt der Ansicht entspricht, die Sie suchen möchten. Ändern Sie dann die entsprechende Eigenschaft im Ressourcen Wörterbuch, und legen Sie die Eigenschaften fest. Stapeln Sie die Aufrufe der- <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> Methode, indem Sie die <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> -Methode aufrufen, bevor Sie die Eigenschaften festlegen, und dann die, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> nachdem Sie die Eigenschaften festgelegt haben.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Erstellen und Testen des Codes  
  
1. Erstellen Sie die Projektmappe.  
  
     Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio instanziiert.  
  
2. Erstellen Sie eine Textdatei, und geben Sie Text ein.  
  
    - Die Einfügemarke muss Magenta lauten, und der über schreibungscaretzeichen sollte Türkis sein.  
  
    - Der Indikator Rand (Links von der Textansicht) sollte hellgrün sein.  
  
3. Wählen Sie den Text aus, den Sie soeben eingegeben haben. Die Farbe des ausgewählten Texts sollte hellrosa sein.  
  
4. Klicken Sie bei ausgewähltem Text auf eine beliebige Stelle außerhalb des Text Fensters. Die Farbe des ausgewählten Texts sollte dunkelrosa sein.  
  
5. Aktivieren Sie sichtbare Leerzeichen. (Zeigen Sie im Menü **Bearbeiten** auf **erweitert** , und klicken Sie dann auf **Leerraum anzeigen**). Geben Sie einige Registerkarten in den Text ein. Rote Pfeile, die die Registerkarten darstellen, sollten angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)
