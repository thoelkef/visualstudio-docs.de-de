---
title: Binden von Daten an Steuerelemente in Office-Projektmappen | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bf5dff37d227e3ba6b07261fc5c1d82b5c679c8b
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
---
# <a name="binding-data-to-controls-in-office-solutions"></a>Binden von Daten an Steuerelemente in Office-Projektmappen
  Sie können Windows Forms-Steuerelemente und *Hoststeuerelemente* auf einem Microsoft Office Word-Dokument oder einem Microsoft Office Excel-Arbeitsblatt an eine Datenquelle binden, sodass die Steuerelemente die Daten automatisch anzeigen. Sie können Daten sowohl in Projekten auf Anwendungsebene als auch in Projekten auf Dokumentebene an Steuerelemente binden.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Hoststeuerelemente erweitern Objekte in den Word- und Excel-Objektmodellen, beispielsweise Inhaltssteuerelemente in Word und benannte Bereiche in Excel. Weitere Informationen finden Sie unter [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 Sowohl in Windows Forms- als auch in Hoststeuerelementen wird das Windows Forms-Datenbindungsmodell verwendet, das sowohl *einfache Datenbindung* als auch *komplexe Datenbindung* an Datenquellen wie Datasets und Datentabellen unterstützt. Vollständige Informationen über das Datenbindungsmodell in Windows Forms finden Sie unter [Datenbindung und Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie führen I: Consume Database Data in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="simple-data-binding"></a>einfache Datenbindung  
 Eine einfache Datenbindung besteht dann, wenn eine Steuerelementeigenschaft an ein einzelnes Datenelement (z. B. einen Wert in einer Datentabelle) gebunden ist. Zum Beispiel hat das <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement die <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft, die an ein Feld in einem Dataset gebunden werden kann. Wenn sich das Feld im Dataset ändert, ändert sich auch der Wert im benannten Bereich. Alle Hoststeuerelemente, mit Ausnahme des <xref:Microsoft.Office.Tools.Word.XMLNodes> -Steuerelements, unterstützen einfache Datenbindung. Das <xref:Microsoft.Office.Tools.Word.XMLNodes> -Steuerelement ist eine Auflistung und unterstützt daher keine Datenbindung.  
  
 Hinzufügen, um einfache Datenbindung an ein Hoststeuerelement auszuführen, eine <xref:System.Windows.Forms.Binding> der DataBindings-Eigenschaft des Steuerelements. Ein <xref:System.Windows.Forms.Binding> -Objekt stellt die einfache Bindung zwischen einem Eigenschaftswert des Steuerelements und dem Wert eines Datenelements dar.  
  
 Im folgenden Beispiel wird veranschaulicht, wie die <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft in einem Projekt auf Dokumentebene an ein Datenelement gebunden wird.  
  
 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]  
  
 Exemplarische Vorgehensweisen, die einfache Datenbindung veranschaulicht wird, finden Sie unter [Exemplarische Vorgehensweise: einfache Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) für ein Projekt auf Dokumentebene und [Exemplarische Vorgehensweise: einfache Datenbindung in einem VSTO-add-in-Projekt ](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) für ein VSTO-Add-in-Projekt.  
  
## <a name="complex-data-binding"></a>komplexe Datenbindung  
 Eine komplexe Datenbindung besteht dann, wenn eine Steuerelementeigenschaft an mindestens zwei Datenelemente (z. B. mehrere Spalten einer Datentabelle) gebunden ist. Das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement für Excel ist das einzige Hoststeuerelement, das komplexe Datenbindung unterstützt. Zudem unterstützen viele Windows Forms-Steuerelemente komplexe Datenbindung, etwa das <xref:System.Windows.Forms.DataGridView> -Steuerelement.  
  
 Um komplexe Datenbindung auszuführen zu können, legen Sie die DataSource-Eigenschaft des Steuerelements auf ein Datenquellenobjekt, das von komplexer Datenbindung unterstützt wird. Beispielsweise kann die <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> -Eigenschaft des <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelements an mehrere Spalten einer Datentabelle gebunden werden. Alle Daten in der Datentabelle werden im <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement angezeigt, und wenn sich die Daten in der Datentabelle ändern, ändert sich auch aus <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement. Eine Liste der Datenquellen, die Sie für komplexe Datenbindung verwenden können, finden Sie unter [Data Sources Supported by Windows Forms](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).  
  
 Im folgenden Codebeispiel wird ein <xref:System.Data.DataSet> mit zwei <xref:System.Data.DataTable> -Objekten erstellt, und eine der Tabellen wird mit Daten aufgefüllt. Im Code wird dann das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement an die Tabelle gebunden, die Daten enthält. Dieses Beispiel gilt für ein Excel-Projekt auf Dokumentebene.  
  
 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]  
  
 Exemplarische Vorgehensweisen, die komplexe Datenbindung veranschaulicht wird, finden Sie unter [Exemplarische Vorgehensweise: komplexe Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) für ein Projekt auf Dokumentebene und [Exemplarische Vorgehensweise: komplexe Datenbindung in einem VSTO-add-in-Projekt ](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) für ein VSTO-Add-in-Projekt.  
  
## <a name="displaying-data-in-documents-and-workbooks"></a>Anzeigen von Daten in Dokumenten und Arbeitsmappen  
 In Projekten auf Dokumentebene können Sie mithilfe des Fensters **Datenquellen** Dokumenten oder Arbeitsmappen datengebundene Steuerelemente auf die gleiche einfache Weise wie für Windows Forms hinzufügen. Weitere Informationen zum Verwenden der **Datenquellen** Fenster finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) und [neue Datenquellen hinzufügen](../data-tools/add-new-data-sources.md).  
  
### <a name="dragging-controls-from-the-data-sources-window"></a>Ziehen von Steuerelementen aus dem Fenster „Datenquellen“  
 Auf einem Dokument wird ein Steuerelement erstellt, wenn Sie aus dem Fenster **Datenquellen** ein Objekt auf das Dokument ziehen. Der Typ des erstellten Steuerelements ist davon abhängig, ob Sie an eine einzelne Datenspalte oder an mehrere Datenspalten binden.  
  
 In Excel werden auf dem Arbeitsblatt ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement für jedes einzelne Feld und für jeden Datenbereich, der mehrere Zeilen und Spalten enthält, ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement erstellt. Sie können diese Standardeinstellung ändern, indem Sie im Fenster **Datenquellen** das Feld oder die Tabelle auswählen und dann in der Dropdownliste ein anderes Steuerelement auswählen.  
  
 Ein <xref:Microsoft.Office.Tools.Word.ContentControl> -Steuerelement wird den Dokumenten hinzugefügt. Der Typ des Inhaltssteuerelements hängt vom Datentyp des von Ihnen ausgewählten Felds ab.  
  
### <a name="binding-data-in-document-level-projects-at-design-time"></a>Binden von Daten in Projekten auf Dokumentebene zur Entwurfszeit  
 In den folgenden Themen werden Beispiele für das Binden von Daten zur Entwurfszeit erläutert:  
  
-   [Vorgehensweise: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)  
  
-   [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)  
  
-   [Vorgehensweise: Auffüllen von Dokumenten mit Daten von Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)  
  
-   [Vorgehensweise: Auffüllen von Dokumente mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
-   [Vorgehensweise: Ausführen eines Bildlaufs durch Datenbankdatensätze in einem Arbeitsblatt](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)  
  
### <a name="binding-data-in-vsto-add-in-projects"></a>Binden von Daten in VSTO-Add-In-Projekten  
 In VSTO-Add-in-Projekten können Sie Steuerelemente nur zur Laufzeit hinzufügen. In den folgenden Themen werden Beispiele für das Binden von Daten zur Laufzeit erläutert:  
  
-   [Exemplarische Vorgehensweise: Einfache Datenbindung in einem VSTO-Add-In-Projekt](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)  
  
-   [Exemplarische Vorgehensweise: Komplexe Datenbindung in einem VSTO-Add-In-Projekt](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)  
  
## <a name="updating-data-that-is-bound-to-host-controls"></a>Aktualisieren von Daten, die an Hoststeuerelemente gebunden ist  
 Eine Datenbindung zwischen einer Datenquelle und einem Hoststeuerelement bedingt eine bidirektionale Datenaktualisierung. Bei einer einfachen Datenbindung werden Änderungen in der Datenquelle automatisch für das Hoststeuerelement übernommen, aber Änderungen im Hoststeuerelement erfordern einen expliziten Aufruf, damit die Datenquelle aktualisiert wird. Dies ist darauf zurückzuführen, dass in einigen Fällen Änderungen in einem datengebundenen Feld nur dann akzeptiert werden, wenn gleichzeitig auch Änderungen in einem anderen datengebundenen Feld vorgenommen werden. Es könnten z. B. zwei Felder vorhanden sein: eines für das Alter und eines für die Jahre an Berufserfahrung. Die Berufserfahrung kann das Alter nicht übersteigen Ein Benutzer kann nur dann das Alter von 50 in 25 und die Berufserfahrung von 30 in 10 ändern, wenn er die Änderungen gleichzeitig vornimmt. Um dieses Problem zu beheben, werden Felder mit einfacher Datenbindung erst aktualisiert, wenn die Aktualisierungen explizit durch Code gesendet wurden.  
  
 Um eine Datenquelle aus Hoststeuerelementen zu aktualisieren, die einfache Datenbindung ermöglichen, müssen Sie Aktualisierungen an die In-Memory-Datenquelle (etwa ein <xref:System.Data.DataSet> oder eine <xref:System.Data.DataTable>) und an die Back-End-Datenbank senden, wenn in Ihrer Projektmappe eine solche verwendet wird.  
  
 Sie müssen die In-Memory-Datenquelle nicht explizit aktualisieren, wenn Sie eine komplexe Datenbindung mit dem <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement ausführen. In diesem Fall werden Änderungen automatisch ohne zusätzlichen Code an die In-Memory-Datenquelle gesendet.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Siehe auch  
 [How Do I: Consume Database Data in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)   
 [Datenbindung und Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)   
 [Vorgehensweise: Erstellen eines einfach gebundenen Steuerelements in einem Windows Form](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Speichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)    
 [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)  
  
  