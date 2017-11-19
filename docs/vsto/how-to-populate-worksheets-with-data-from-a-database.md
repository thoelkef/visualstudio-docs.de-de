---
title: "Vorgehensweise: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b7cfb842a0372d4410a0794ff8ade901af713b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank
  Sie können Daten in Office-Projekten auf Dokumentebene auf die gleiche Weise zugreifen, dass Sie in Windows Forms-Projekten Datenzugriff. Sie verwenden dieselben Tools und denselben Code, um die Daten in die Projektmappe einzufügen, und können außerdem Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie nutzen genannten Hoststeuerelemente, die systemeigene Objekte in Microsoft Office Excel sind, die mit Ereignissen und Datenbindung Funktion erweitert wurden. Weitere Informationen finden Sie unter [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Das folgende Beispiel zeigt, wie Sie datengebundene Steuerelemente in Projekten auf Dokumentebene mithilfe eines Designers hinzufügen. Ein Beispiel zum Hinzufügen von datengebundenen Steuerelementen in Projekten auf Anwendungsebene zur Laufzeit finden Sie unter [Exemplarische Vorgehensweise: komplexe Datenbindung in einem VSTO-add-in-Projekt](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie führen I: übertragen Daten in ein Excel-Arbeitsblatt?](http://go.microsoft.com/fwlink/?LinkID=130277), und [wie führen I: Consume Database Data in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## <a name="adding-a-data-bound-control-to-a-worksheet-at-design-time"></a>Hinzufügen eines datengebundenen Steuerelements zu einem Arbeitsblatt zur Entwurfszeit  
  
#### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Um ein Arbeitsblatt mit Daten aus einer Datenbank aufzufüllen.  
  
1.  Öffnen Sie ein Excel-Projekt auf Dokumentebene in Visual Studio, mit dem Arbeitsblatt im Designer geöffnet.  
  
2.  Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie für Ihr Projekt eine Datenquelle. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).  
  
3.  Ziehen Sie das Feld oder die Tabelle aus der **Datenquellen** in das Arbeitsblatt.  
  
 Eines der folgenden Steuerelemente auf dem Arbeitsblatt erstellt:  
  
-   Wenn Sie ein Feld Ziehen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement auf das Arbeitsblatt erstellt wird. Weitere Informationen finden Sie unter [NamedRange-Steuerelement](../vsto/namedrange-control.md).  
  
-   Wenn Sie eine Tabelle Ziehen einer <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement auf das Arbeitsblatt erstellt wird. Weitere Informationen finden Sie unter [ListObject Control](../vsto/listobject-control.md).  
  
 Sie können das Feld oder ein anderes Steuerelement hinzufügen, indem Sie die Tabelle auswählen der **Datenquellen** Fenster und dann ein anderes Steuerelement in der Dropdownliste auswählen.  
  
## <a name="objects-in-the-project"></a>Objekte im Projekt  
 Neben dem Steuerelement werden die folgenden datenbezogenen Objekte dem Projekt automatisch hinzugefügt:  
  
-   Ein typisiertes Dataset, das die Datentabellen kapselt, mit denen Sie in der Datenbank eine Verbindung hergestellt haben. Weitere Informationen finden Sie unter [Dataset-Tools in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
-   Eine <xref:System.Windows.Forms.BindingSource>, durch die das Steuerelement mit dem typisierten Dataset verbunden wird. Weitere Informationen finden Sie unter [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
-   Ein TableAdapter, der das typisierte Dataset mit der Datenbank verbunden. Weitere Informationen finden Sie unter [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
-   Einen TableAdapterManager dient zum Koordinieren von Tabellenadaptern im Dataset, um hierarchische Updates zu aktivieren. Weitere Informationen finden Sie unter [hierarchische Aktualisierung](../data-tools/hierarchical-update.md) und [TableAdapterManager Verweis](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).  
  
 Beim Ausführen des Projekts zeigt das Steuerelement den ersten Datensatz in der Datenquelle an. Sie können die <xref:System.Windows.Forms.BindingSource> verwenden, um Benutzern einen Bildlauf in den Datensätzen zu ermöglichen.  
  
#### <a name="to-scroll-through-the-records"></a>So führen Sie einen Bildlauf durch die Datensätze durch  
  
-   Verwenden Sie <xref:System.Windows.Forms.BindingSource>-Methoden wie <xref:System.Windows.Forms.BindingSource.MoveNext%2A> und <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Informationen zum Senden von Updates für das typisierte Dataset und die Datenbank finden Sie unter [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Neue Datenquellen hinzufügen](/visualstudio/data-tools/add-new-data-sources)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Wie I: Daten in einem Excel-Arbeitsblatt übertragen](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Wie nutzen I: Database Data in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  