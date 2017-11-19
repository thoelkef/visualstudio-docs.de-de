---
title: Bookmark-Steuerelement | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
ms.assetid: 940bf165-18c9-4db8-a46c-aad786b8bbad
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d846c1a0a52011991d231e567c1727e456a1feee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="bookmark-control"></a>Bookmark-Steuerelement
  Das <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement ist eine Textmarke, die über einen eindeutigen Namen verfügt, Ereignisse verfügbar macht und an Daten gebunden werden kann. Die Textmarke kann als Platzhalter verwendet werden, um ein Element oder eine Position in einem Microsoft Office Word-Dokument zu markieren. Das <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement ist eine Kombination aus einem <xref:Microsoft.Office.Interop.Word.Bookmark> - und einem <xref:Microsoft.Office.Interop.Word.Range> -Objekt.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 In Projekten auf Dokumentebene können Sie dem Dokument <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelemente zur Entwurfszeit oder zur Laufzeit hinzufügen. In VSTO-Add-In-Projekten können Sie einem beliebigen geöffneten Dokument zur Laufzeit <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelemente hinzufügen. Weitere Informationen finden Sie unter [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
## <a name="binding-data-to-the-control"></a>Binden von Daten an das Steuerelement  
 Ein <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement unterstützt die einfache Datenbindung. Die Textmarke sollte mithilfe der <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> -Eigenschaft an eine Datenquelle gebunden werden. Die Standardeigenschaft für die Datenbindung der Textmarke ist die <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> -Eigenschaft.  
  
 Wenn die Daten im gebundenen DataSet aktualisiert werden, spiegelt das <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement die Änderungen wider.  
  
 In Projekten auf Dokumentebene können Sie Daten auch an Textmarken binden, indem Sie das Fenster **Datenquellen** verwenden. Weitere Informationen finden Sie unter [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
## <a name="formatting"></a>Formatierung  
 Die auf <xref:Microsoft.Office.Interop.Word.Bookmark> anwendbare Formatierung kann auf ein <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement angewendet werden. Dies schließt Schriftarten, Einzüge, Abstände, Nummerierungen und Formatvorlagen ein.  
  
## <a name="assigning-text-to-the-bookmark"></a>Zuweisen von Text zur Textmarke  
 Ein weiterer Unterschied zwischen einem <xref:Microsoft.Office.Interop.Word.Bookmark> -Objekt und einem <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement ist das Verhalten beim Zuweisen von Text zur Textmarke. Wenn Sie Text zu einem <xref:Microsoft.Office.Interop.Word.Bookmark>mit der Länge 0 (null) zuweisen, wird der Text rechts neben der Textmarke angefügt und die Textmarke behält die Länge 0 (null). Wenn Sie jedoch Text zu einem <xref:Microsoft.Office.Tools.Word.Bookmark>mit der Länge 0 (null) zuweisen, wird der Text in die Textmarke eingefügt und die Länge der Textmarke um die Gesamtzahl der eingefügten Zeichen erweitert.  
  
 Das <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement verfügt auch über die <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> -Eigenschaft. Dieses unterscheidet sich von der <xref:Microsoft.Office.Interop.Word.Range.Text%2A> -Eigenschaft, die für die <xref:Microsoft.Office.Tools.Word.Bookmark.Range%2A> -Eigenschaft eines <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelements oder für die <xref:Microsoft.Office.Interop.Word.Bookmark.Range%2A> -Eigenschaft eines <xref:Microsoft.Office.Interop.Word.Bookmark> -Objekts verfügbar ist.  
  
|Text-Eigenschaft|Beschreibung|  
|-------------------|-----------------|  
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>|Verwenden Sie diese Eigenschaft zum Anzeigen von Text in einer Textmarke, und belassen Sie die Textmarke im Dokument. Durch das Zuweisen von Text zur Textmarke wird der Textmarkenbereich erweitert und die Textmarke nicht gelöscht.<br /><br /> `Bookmark1.Text = "Hello world"` fügt z. B. den Text in die Textmarken ein, und die Textmarke bleibt intakt.|  
|<xref:Microsoft.Office.Interop.Word.Range.Text%2A>|Verwenden Sie diese Eigenschaft, um Text an der Position der Textmarke anzuzeigen und die Textmarke automatisch zu löschen. `Bookmark1.Range.Text = "Hello world"` fügt z. B. den Text in die Textmarke ein, und die Textmarke wird gelöscht.|  
  
## <a name="renaming-the-control-at-design-time"></a>Umbenennen des Steuerelements zur Entwurfszeit  
 Wenn Sie in Projekten auf Dokumentebene ein <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement aus der **Toolbox** in Ihr Dokument ziehen, generiert Visual Studio automatisch einen Namen für das Steuerelement. Sie können den Namen des Steuerelemente im Fenster **Eigenschaften** ändern.  
  
## <a name="overlapping-controls"></a>Überlappende Steuerelemente  
 Bookmark-Steuerelemente können einander überlappen. Das bedeutet, dass derselbe Text von mehreren Textmarken gemeinsam genutzt werden kann. Wenn Sie einer der überlappenden Textmarken neuen Text zuweisen, dann enthält sie nur den neuen Text und die Textmarken überlappen nicht mehr. Die andere Textmarke enthält jetzt nur den Text, der nicht von der ursprünglich überlappenden Textmarke gemeinsam genutzt wurde.  
  
 In der folgenden Tabelle wird gezeigt, wie der Satz „This is sample text.“ von zwei überlappenden Textmarken gemeinsam genutzt wird.  
  
|Textmarke|Text|  
|--------------|----------|  
|Überlappende Textmarken|[this is {sample] text.}|  
|Bookmark1|This is sample|  
|Bookmark2|sample text.|  
  
 Wenn Sie den neuen Text „This is replacement." zu Bookmark1 zuweisen, überlappen die Textmarken nicht länger und Bookmark2 behält nur den Text, der ursprünglich nicht Teil von Bookmark1 war.  
  
|Textmarke|Text|  
|--------------|----------|  
|Zwei separate Textmarken|[this is replacement]{ text.}|  
|Bookmark1|This is replacement|  
|Bookmark2|text.|  
  
 Wenn eine Textmarke vollständig in einer anderen Textmarke enthalten ist und Sie den Text der äußeren Textmarke ändern, wird die innere Textmarke nicht gelöscht. Die innere Textmarke wird jedoch zu einer leeren Textmarke, die an das Ende der äußeren Textmarke verschoben wird. In der folgenden Tabelle wird gezeigt, wie der Satz „This is sample text.“ von einer Textmarke gemeinsam genutzt wird, die in einer anderen Textmarke enthalten ist.  
  
|Textmarke|Text|  
|--------------|----------|  
|Überlappende Textmarken|[this is {sample} text.]|  
|Bookmark1|This is sample text.|  
|Bookmark2|Beispiel|  
  
 Wenn Sie den neuen Text „This is replacement." zu Bookmark1 zuweisen, überlappen sich die Textmarken nicht mehr, und Bookmark2 wird zu einer leeren Textmarke, die sich am Ende von Bookmark1 befindet.  
  
|Textmarke|Text|  
|--------------|----------|  
|Zwei separate Textmarken|[this is replacement.]{}|  
|Bookmark1|This is replacement.|  
|Bookmark2|*\<leere >*|  
  
## <a name="events"></a>Ereignisse  
 Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement verfügbar:  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>  
  
-   <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Exemplarische Vorgehensweise: Erstellen von Kontextmenüs für Lesezeichen](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  