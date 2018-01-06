---
title: "Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Diensten | Microsoft Docs"
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
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
ms.assetid: 4c42653c-627f-445e-9024-8482eaf5562e
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5cdcfc080251d62bf0f7dbede2016b4821383c5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Gewusst wie: Auffüllen von Dokumente mit Daten aus Diensten
  Der Datenzugriff funktioniert in Microsoft Office-Projekten auf Dokumentebene auf die gleiche Weise wie in Windows Forms-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten in die Projektmappe einzufügen, und können außerdem Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie von so genannten Hoststeuerelemente profitieren – systemeigene Objekte in Microsoft Office Excel und Microsoft Office Word, die um Ereignisse und Datenbindungsfunktionen erweitert wurden. Weitere Informationen finden Sie unter [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Das folgende Beispiel zeigt, wie Sie Dokumenten zur Entwurfszeit datengebundene Steuerelemente hinzufügen. Ein Beispiel zum Hinzufügen von datengebundenen Steuerelementen in VSTO-Add-ins zur Laufzeit finden Sie unter [Exemplarische Vorgehensweise: Binden an Daten aus einem Dienst in einem VSTO-add-in Project](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [Anleitung: interagieren mit Webdiensten aus Microsoft Excel?](http://go.microsoft.com/fwlink/?LinkID=130284).  
  
### <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>So füllen Sie ein Projekt auf Dokumentebene mit Daten aus einem Webdienst auf  
  
1.  Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie für Ihr Projekt eine Dienstdatenquelle. Weitere Informationen finden Sie unter [Neue Datenquelle hinzufügen](/visualstudio/data-tools/add-new-data-sources).  
  
2.  Ziehen Sie die gewünschte Tabelle oder das gewünschte Feld vom Fenster **Datenquellen** in Ihr Dokument.  
  
     Im Dokument wird ein Steuerelement erstellt. Zudem werden für den Dienst eine an die Objektklassen des Projekts gebundene <xref:System.Windows.Forms.BindingSource> und Klassen generiert.  
  
3.  Erstellen Sie im Code eine Instanz der Webdienstklasse, zu der in Schritt 1 eine Verbindung hergestellt wurde.  
  
4.  Wenn für die Kommunikation mit dem Webdienst Eigenschaften erforderlich sind, erstellen Sie Instanzen dieser Eigenschaften.  
  
5.  Erstellen und senden Sie mithilfe der vom Webdienst bereitgestellten Methoden und der in Schritt 4 erstellten Dateninstanzen eine Datenanforderung.  
  
     Welche Methoden verwendet werden, ist abhängig vom Angebot des Webdiensts.  
  
6.  Weisen Sie die Datenantwort des Webdiensts der Eigenschaft <xref:System.Windows.Forms.BindingSource.DataSource%2A> der <xref:System.Windows.Forms.BindingSource>zu.  
  
 Wenn Sie das Projekt ausführen, zeigen die Steuerelemente den ersten Datensatz in der Datenquelle an. Sie können einen Bildlauf durch die Datensätze ermöglichen, indem Sie die „Currency“-Ereignisse mit den Objekten in der <xref:System.Windows.Forms.BindingSource>verarbeiten.  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Neue Datenquellen hinzufügen](/visualstudio/data-tools/add-new-data-sources)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vorgehensweise: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)  
  
  