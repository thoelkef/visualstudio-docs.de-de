---
title: XML-Schemas und Daten in Anpassungen auf Dokumentebene
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: e62a8a7bef72ce34c46621b63188f9d71512be20
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672656"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>XML-Schemas und Daten in Anpassungen auf Dokumentebene
  **Wichtige** die Informationen in diesem Thema nach Microsoft Word festgelegt ist, ausschließlich für die Vorteile und die Verwendung von Einzelpersonen und Organisationen, die außerhalb der Vereinigten Staaten und seine Gebiete befinden oder mit, dargestellten oder entwickeln Programme, auf denen ausgeführt wird, im Zusammenhang mit benutzerdefinierten XML-Code aus Microsoft Word Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden, wenn Microsoft eine Implementierung von bestimmten Funktionen entfernt. Diese Informationen in Bezug auf Microsoft Word kann nicht gelesen oder durch Einzelpersonen oder Organisationen, die in den Vereinigten Staaten oder der Gebiete, die mithilfe von, oder Entwickeln von Anwendungen, die Microsoft Word-Produkte ausgeführt werden, die von Microsoft, nach dem 10. Januar 2010 lizenziert wurden verwendet werden ; Diese Produkte verhält nicht als Produkte, die vor diesem Datum lizenziert oder erworben und für die Verwendung außerhalb der USA lizenziert.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel und Microsoft Office Word bieten die Möglichkeit, Ihre Dokumente Schemas zuzuordnen. Dieses Feature kann vereinfachen, importieren und Exportieren von XML-Daten in und aus dem Dokument.  
  
 Visual Studio verfügbar gemacht werden Elemente des Schemas in Anpassungen auf Dokumentebene als Steuerelemente in das Programmiermodell zugeordnet. Für Excel fügt Visual Studio-Unterstützung für das Binden von Steuerelementen an Daten in Datenbanken, Webdienste und Objekte. Für Word und Excel fügt Visual Studio-Unterstützung für Aktionsbereiche, die mit einem zugeordneten Schema-Dokument verwendet werden kann, um eine verbesserte benutzerfreundlichkeit für Ihre Lösungen zu erstellen. Weitere Informationen finden Sie unter [aktionsbereichsübersicht](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  Sie können keine mehrteiligen XML-Schemas in Excel-Projektmappen verwenden.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objekte, die erstellt, wenn Sie Schemas mit Excel-Arbeitsmappen verbunden sind  
 Wenn Sie ein Schema mit einer Arbeitsmappe anfügen, werden von Visual Studio automatisch mehrere Objekte erstellt und dem Projekt hinzugefügt. Diese Objekte sollten nicht gelöscht werden mithilfe von Visual Studio-Tools, das, weil sie von Excel verwaltet werden ist. Um diese zu löschen, entfernen Sie die zugeordneten Elemente aus dem Arbeitsblatt aus, oder trennen Sie das Schema mithilfe von Excel-Tools.  
  
 Es gibt zwei Hauptobjekten:  
  
-   XML-Schema (XSD-Datei). Für jedes Schema in der Arbeitsmappe wird dem Projekt mit Visual Studio ein Schema hinzugefügt. Dies wird als ein Projektelement mit der Erweiterung XSD in **Projektmappen-Explorer**.  
  
-   Eine typisierte <xref:System.Data.DataSet>-Klasse. Diese Klasse wird basierend auf dem Schema erstellt. Dieses Dataset-Klasse werden in **Klassenansicht**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objekte, die erstellt, wenn die Elemente des Schemas zu Excel-Arbeitsblättern zugeordnet sind  
 Beim Zuordnen einer Schema-Element aus der **XML-Quelle** Aufgabenbereich zu einem Arbeitsblatt, Visual Studio automatisch mehrere Objekte erstellt, und fügt sie dem Projekt hinzu:  
  
-   Steuerelemente Für jedes zugeordnete Objekt in der Arbeitsmappe eine <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement (für nicht wiederholte Schemaelemente) oder ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement (für sich wiederholende Elemente des Schemas) in das Programmiermodell, das erstellt wird. Die <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement kann nur durch Löschen von Zuordnungen und die zugeordneten Objekte aus der Arbeitsmappe gelöscht werden. Weitere Informationen zu Steuerelementen, finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource. Bei der Erstellung einer <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> durch ein nicht wiederholendes Schemaelement zuordnen, in das Arbeitsblatt, ein <xref:System.Windows.Forms.BindingSource> wird erstellt und die <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> -Steuerelement gebunden ist, die <xref:System.Windows.Forms.BindingSource>. Sie müssen das Binden der <xref:System.Windows.Forms.BindingSource> mit einer Instanz von der Datenquelle, die dem Schema zugeordnet, auf das Dokument, z. B. eine Instanz des typisierten <xref:System.Data.DataSet> -Klasse, die erstellt wurde. Erstellen Sie die Bindung durch Festlegen der <xref:System.Windows.Forms.BindingSource.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> Eigenschaften, die in verfügbar gemacht werden die **Eigenschaften** Fenster.  
  
    > [!NOTE]  
    >  Die <xref:System.Windows.Forms.BindingSource> wird nicht für erstellt <xref:Microsoft.Office.Tools.Excel.ListObject> Objekte. Sie müssen manuell binden die <xref:Microsoft.Office.Tools.Excel.ListObject> an die Datenquelle durch Festlegen der <xref:System.Windows.Forms.BindingSource.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> Eigenschaften in der **Eigenschaften** Fenster.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office zugeordnet, Schemas und das Visual Studio-Datenquellen-Fenster  
 Sowohl die zugeordneten Schema-Funktionalität von Office und Visual Studio **Datenquellen** Fenster können Sie die präsentieren von Daten in einem Excel-Arbeitsblatt für die berichterstellung oder zu bearbeiten. In beiden Fällen können Sie Datenelemente in das Excel-Arbeitsblatt ziehen. Beide Methoden Steuerelemente erstellen, die über Daten gebunden sind eine <xref:System.Windows.Forms.BindingSource> mit einer Datenquelle, z. B. eine <xref:System.Data.DataSet> oder einen Webdienst.  
  
> [!NOTE]  
>  Wenn Sie einem Arbeitsblatt ein sich wiederholendes Schemaelement zuordnen, erstellt Visual Studio eine <xref:Microsoft.Office.Tools.Excel.ListObject>. Die <xref:Microsoft.Office.Tools.Excel.ListObject> nicht automatisch an Daten gebunden ist die <xref:System.Windows.Forms.BindingSource>. Sie müssen manuell binden die <xref:Microsoft.Office.Tools.Excel.ListObject> an die Datenquelle durch Festlegen der <xref:System.Windows.Forms.BindingSource.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> Eigenschaften in der **Eigenschaften** Fenster.  
  
 Die folgende Tabelle zeigt einige der Unterschiede zwischen den beiden Methoden.  
  
|XML-schema|Datenquellenfenster|  
|----------------|-------------------------|  
|Office-Benutzeroberfläche verwendet.|Verwendet **Datenquellen** Fenster in Visual Studio.|  
|Können die integrierten Office-Features für das Importieren und Exportieren von Daten aus XML-Dateien.|Sie müssen Funktionen programmgesteuert exportieren und Importieren angeben.|  
|Sie müssen den Code aus, um die generierten Steuerelemente mit Daten füllen schreiben.|Steuerelemente hinzugefügt wurden, aus der **Datenquellen** ist Code, um die Felder auszufüllen, zusammen mit der benötigten Verbindungszeichenfolgen, bei der Verwendung von Datenbank-Server automatisch generiert.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Verhalten, wenn die Schemas zu Word-Dokumenten angefügt sind  
 Datenobjekte werden nicht erstellt werden, wenn Sie ein Schema in ein Word-Dokument anfügen, die in einem Office-Projekt auf Dokumentebene verwendet wird. Wenn Sie ein Element des Schemas in Ihr Dokument zuordnen, werden Steuerelemente jedoch erstellt. Der Typ des Steuerelements hängt vom Typ des Elements, die Sie zuordnen; Wiederholen die Elemente generieren <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelemente und nicht wiederholte Elemente generieren <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelemente. Weitere Informationen finden Sie unter [XMLNodes-Steuerelement](../vsto/xmlnodes-control.md) und [XMLNode-Steuerelement](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Bereitstellung von Projektmappen, die XML-Schemas enthalten.  
 Erstellen Sie ein Installationsprogramm zum Bereitstellen einer Lösung, die ein XML-Schema verwendet, die einem Dokument zugeordnet ist. Der Installer sollten das Schema in der Schemabibliothek auf dem Computer des Benutzers registrieren. Wenn Sie das Schema nicht registrieren, wird die Lösung weiterhin funktionieren, da Word ein temporäres Schema basierend auf die Elemente, die im Dokument sind generiert, wenn der Benutzer sie öffnet. Allerdings wird der Benutzer nicht zum Validieren von oder speichern Sie das Schema, das zum Erstellen des Projekts verwendet wurde. Weitere Informationen zu installern finden Sie unter [Bereitstellen von Anwendungen, Diensten und Komponenten](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 Sie können auch Code hinzufügen, um Ihr Projekt zu überprüfen, ob das Schema in der Bibliothek ist und registriert. Wenn sie nicht der Fall ist, können Sie die Benutzer warnen.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  
