---
title: "Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten | Microsoft Docs"
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
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 02f2b735ceb473f7ffe55345c1cd45dc084edb80
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Gewusst wie: Auffüllen von Dokumenten mit Daten von Objekten
  Der Zugriff auf Daten in einem Datenobjekt funktioniert in Microsoft Office Word-Projekten auf Dokumentebene auf die gleiche Weise wie in Windows Forms-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten aus einem Objekt in die Projektmappe einzufügen, und können Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie Daten mithilfe von Hoststeuerelementen anzeigen. Hoststeuerelemente sind systemeigene Objekte in Microsoft Office Word, die mit Ereignissen und Datenbindungsfunktion erweitert wurden. Weitere Informationen finden Sie unter [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Sie müssen drei grundlegende Schritte ausführen, um das Dokument mit Daten aus einem Objekt aufzufüllen:  
  
-   Fügen Sie ein Steuerelement zum Dokument hinzu, das an Daten gebunden werden kann.  
  
-   Fügen Sie ein Datenobjekt zum Dokument hinzu.  
  
-   Verbinden Sie das Datenobjekt mit der BindingSource-Komponente.   
  
## <a name="adding-a-data-object"></a>Hinzufügen eines Datenobjekts  
  
#### <a name="to-add-a-data-object"></a>So fügen Sie ein Datenobjekt hinzu  
  
-   Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie eine Datenquelle auf Grundlage eines Objekts. Weitere Informationen finden Sie unter [Neue Datenquelle hinzufügen](/visualstudio/data-tools/add-new-data-sources).  
  
## <a name="connecting-the-data-object-to-the-bindingsource"></a>Verbinden des Datenobjekts mit der BindingSource-Komponente  
 In Projekten auf Dokumentebene fügen Sie Ihrem Dokument Steuerelemente hinzu und binden diese zur Entwurfszeit an Daten.  
  
 In VSTO-Add-In-Projekten erstellen Sie Steuerelemente und binden diese zur Laufzeit.  
  
### <a name="document-level-projects"></a>Projekte auf Dokumentebene  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>So verbinden Sie das Datenobjekt mit der BindingSource-Komponente  
  
1.  Ziehen Sie das gewünschte Datenfeld vom Fenster **Datenquellen** in Ihr Dokument. Dadurch wird automatisch ein Steuerelement erstellt.  
  
2.  Erstellen Sie im Code eine Instanz des Typs des Objekts, das Sie für die Datenquelle ausgewählt haben.  
  
3.  Weisen Sie die Instanz der <xref:System.Windows.Forms.BindingSource.DataSource%2A> -Eigenschaft der <xref:System.Windows.Forms.BindingSource>-Komponente zu.  
  
### <a name="application-level-projects"></a>Projekte auf Anwendungsebene  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>So verbinden Sie das Datenobjekt mit der BindingSource-Komponente  
  
1.  Erstellen Sie im Code eine Instanz des Typs des Objekts, das der Datenquelle zugewiesen wird.  
  
2.  Erstellen Sie eine Instanz einer <xref:System.Windows.Forms.BindingSource>-Komponente:  
  
3.  Weisen Sie die Datenquelleninstanz der <xref:System.Windows.Forms.BindingSource.DataSource%2A> -Eigenschaft der <xref:System.Windows.Forms.BindingSource>-Komponente zu.  
  
4.  Fügen Sie die Datenquelle als eine Datenbindung zum Steuerelement hinzu.  
  
## <a name="see-also"></a>Siehe auch  
 
 [Neue Datenquellen hinzufügen](/visualstudio/data-tools/add-new-data-sources)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Stduio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)
 
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Herstellen einer Verbindung mit Daten in Windows Forms-Anwendungen](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  