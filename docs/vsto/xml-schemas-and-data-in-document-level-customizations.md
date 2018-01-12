---
title: XML-Schemas und Daten in Anpassungen auf Dokumentebene | Microsoft Docs
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
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b3f55c8c6b2975e8dbaa85177fddcadaf62e000e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML-Schemas und -Daten in Anpassungen auf Dokumentebene
  **Wichtige** die Informationen in diesem Thema nach Microsoft Word wird dargestellten ausschließlich für die Vorteile und die Verwendung von Einzelpersonen und Organisationen, die außerhalb der Vereinigten Staaten und seine Gebiete befinden, oder verwenden, oder entwickeln Programme, die unter ausgeführt, im Zusammenhang mit benutzerdefinierten XML-Code von Microsoft Word Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden, wenn eine Implementierung der einzelnen Funktionen von Microsoft entfernt. Diese Informationen bezüglich Microsoft Word kann nicht gelesen oder von Einzelpersonen oder Organisationen aus, in den Vereinigten Staaten oder die Vertriebsgebiete, denen der verwenden, oder entwickeln Programme, die auf Microsoft Word-Produkte ausgeführt, die von Microsoft nach dem 10. Januar 2010 lizenziert wurden verwendet werden ; Diese Produkte verhält sich nicht wie Produkte, die vor diesem Datum lizenziert oder erworben und lizenziert für die Verwendung außerhalb der Vereinigten Staaten.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel und Microsoft Office Word bieten die Möglichkeit, Ihre Dokumente Schemas zuzuordnen. Diese Funktion kann vereinfachen, importieren und Exportieren von XML-Daten in und aus dem Dokument.  
  
 Visual Studio stellt Steuerelemente im Programmiermodell Schemaelemente in Anpassungen auf Dokumentebene zugeordnet. Für Excel fügt Visual Studio-Unterstützung für das Binden von Steuerelementen an Daten in Datenbanken, Webdiensten und Objekten. Für Word und Excel fügt Visual Studio-Unterstützung für Aktionsbereiche, die mit einem zugeordneten Schema-Dokument verwendet werden kann, um eine verbesserte Benutzeroberfläche zur für Ihre Lösungen zu erstellen. Weitere Informationen finden Sie unter [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  Sie können keine mehrteiligen XML-Schemas in Excel-Projektmappen.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objekte erstellt, wenn Excel-Arbeitsmappen Schemas zugeordnet sind  
 Wenn Sie ein Schema mit einer Arbeitsmappe anfügen, werden von Visual Studio automatisch mehrere Objekte erstellt und dem Projekt hinzugefügt. Diese Objekte sollten nicht mit gelöscht werden Visual Studio-Tools, da sie von Excel verwaltet werden. Um diese zu löschen, entfernen Sie die zugeordneten Elemente aus dem Arbeitsblatt, oder trennen Sie das Schema mithilfe von Excel-Tools.  
  
 Es gibt zwei Hauptobjekte:  
  
-   XML-Schema (XSD-Datei). Für jedes Schema in der Arbeitsmappe fügt Visual Studio ein Schema zum Projekt hinzu. Dies wird als ein Projektelement mit einer XSD-Erweiterung im **Projektmappen-Explorer**.  
  
-   Eine typisierte <xref:System.Data.DataSet>-Klasse. Diese Klasse wird basierend auf dem Schema erstellt. Dieses Dataset-Klasse werden in **Klassenansicht**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objekte erstellt, wenn Excel-Arbeitsblättern Schemaelemente zugeordnet sind  
 Wenn Sie ein Element des Schemas aus Zuordnen der **XML-Quelle** Aufgabenbereich zu einem Arbeitsblatt, Visual Studio automatisch mehrere Objekte erstellt und dem Projekt hinzugefügt:  
  
-   Steuerelemente Für jedes zugeordnete Objekt in der Arbeitsmappe eine <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> -Steuerelement (für nicht wiederholte Schemaelemente) oder ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement (für sich wiederholende Schemaelemente) im Programmiermodell erstellt wird. Die <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement kann nur durch das Löschen von Zuordnungen und die zugeordneten Objekte aus der Arbeitsmappe gelöscht werden. Weitere Informationen zu Steuerelementen finden Sie unter [Host Steuerelemente Übersicht über Hostelemente und](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource-Komponente. Beim Erstellen einer <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> durch ein nicht wiederholendes Schemaelement zuordnen, in das Arbeitsblatt ein <xref:System.Windows.Forms.BindingSource> wird erstellt und die <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> gebunden ist die <xref:System.Windows.Forms.BindingSource>. Binden Sie die <xref:System.Windows.Forms.BindingSource> mit einer Instanz von der Datenquelle, die das Schema, das Dokument, z. B. eine Instanz des typisierten zugeordnet entspricht <xref:System.Data.DataSet> -Klasse, die erstellt wurde. Erstellen Sie die Bindung durch Festlegen der <xref:System.Windows.Forms.BindingSource.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> Eigenschaften, die in verfügbar gemacht werden die **Eigenschaften** Fenster.  
  
    > [!NOTE]  
    >  Die <xref:System.Windows.Forms.BindingSource> wird nicht für erstellt <xref:Microsoft.Office.Tools.Excel.ListObject> Objekte. Müssen Sie manuell Binden der <xref:Microsoft.Office.Tools.Excel.ListObject> mit der Datenquelle durch Festlegen der <xref:System.Windows.Forms.BindingSource.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> Eigenschaften in der **Eigenschaften** Fenster.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office zugeordnet, Schemas und der Visual Studio-Datenquellenfenster  
 Sowohl die zugeordneten Schema-Funktionalität von Office und Visual Studio **Datenquellen** Fenster können Sie die präsentieren von Daten in einem Excel-Arbeitsblatt zu Berichts- oder zu bearbeiten. In beiden Fällen können Sie Datenelemente in das Excel-Arbeitsblatt ziehen. Beide Methoden erstellen Sie Steuerelemente, die über Daten gebunden sind eine <xref:System.Windows.Forms.BindingSource> mit einer Datenquelle, z. B. eine <xref:System.Data.DataSet> oder einen Webdienst.  
  
> [!NOTE]  
>  Wenn Sie einem Arbeitsblatt ein sich wiederholendes Schemaelement zuordnen, erstellt Visual Studio eine <xref:Microsoft.Office.Tools.Excel.ListObject>. Die <xref:Microsoft.Office.Tools.Excel.ListObject> nicht automatisch an Daten gebunden ist die <xref:System.Windows.Forms.BindingSource>. Müssen Sie manuell Binden der <xref:Microsoft.Office.Tools.Excel.ListObject> mit der Datenquelle durch Festlegen der <xref:System.Windows.Forms.BindingSource.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> Eigenschaften in der **Eigenschaften** Fenster.  
  
 Die folgende Tabelle zeigt einige Unterschiede zwischen den beiden Methoden.  
  
|XML-schema|Datenquellenfenster|  
|----------------|-------------------------|  
|Office-Benutzeroberfläche verwendet.|Verwendet **Datenquellen** Fenster in Visual Studio.|  
|Aktiviert die integrierten Office-Funktionen zum Importieren und Exportieren von Daten aus XML-Dateien.|Sie müssen Funktionalität programmgesteuert exportieren und Importieren angeben.|  
|Sie müssen den Code aus, um die generierten Steuerelemente mit Daten füllen schreiben.|Steuerelemente hinzugefügt wurden, aus der **Datenquellen** Fenster haben, um Sie auszufüllen, zusammen mit den erforderlichen Verbindungszeichenfolgen bei der Verwendung von Datenbankservern automatisch generierten Code.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Verhalten beim Schemas zu Word-Dokumenten angefügt sind  
 Datenobjekte werden nicht erstellt werden, wenn Sie ein Schema zu einem Worddokument anfügen, die in einem Office-Projekt auf Dokumentebene verwendet wird. Wenn Sie Ihrem Dokument ein Schemaelement zuordnen, werden jedoch Steuerelemente erstellt. Der Typ des Steuerelements hängt vom Typ des Elements, die Sie zuordnen; wiederholte Elemente generieren <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelemente und nicht wiederholte Elemente generieren <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelemente. Weitere Informationen finden Sie unter [XMLNodes-Steuerelement](../vsto/xmlnodes-control.md) und [XMLNode-Steuerelement](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Bereitstellen von Lösungen, die XML-Schemas enthalten.  
 Erstellen Sie ein Installationsprogramm aus, um eine Lösung bereitstellen, die ein XML-Schema verwendet, die zu einem Dokument zugeordnet ist. Der Installer sollten das Schema in der Schemabibliothek auf dem Computer des Benutzers registrieren. Wenn Sie das Schema nicht registrieren, wird die Projektmappe weiterhin funktionieren, da Word ein temporäres Schema basierend auf den Elementen, die im Dokument sind generiert, wenn der Benutzer geöffnet wird. Allerdings wird der Benutzer nicht zum Validieren von oder speichern Sie das Schema, das zum Erstellen des Projekts verwendet wurde. Weitere Informationen zu installern finden Sie unter [Bereitstellen von Anwendungen, Diensten und Komponenten](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 Sie können auch Code hinzufügen, um das Projekt zu überprüfen, ob das Schema in der Bibliothek ist und registriert. Wenn sie nicht der Fall ist, können Sie die Benutzer warnen.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Vorgehensweise: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  