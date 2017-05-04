---
title: "XML-Schemas und -Daten in Anpassungen auf Dokumentebene | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office-Entwicklung in Visual Studio, XML"
  - "Schemas [Office-Entwicklung in Visual Studio]"
  - "XML [Office-Entwicklung in Visual Studio], XML-Schemas"
  - "XML-Schemas [Office-Entwicklung in Visual Studio]"
  - "XML-Schemas [Office-Entwicklung in Visual Studio], Informationen über XML-Schemas and Daten"
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# XML-Schemas und -Daten in Anpassungen auf Dokumentebene
  **Wichtig** die Informationen, die in diesem Thema bezüglich Microsoft Word erläutert werden, wird ausschließlich für den Nutzen und die Verwendung von Personen und Organisationen, die außerhalb der USA und ihrer Außengebiete befinden, oder die verwenden, oder entwickeln Programme, die auf ausgeführt werden, Microsoft Word\-Produkte dargestellt, die von Microsoft vor Januar 2010 lizenziert wurden, als Microsoft eine Implementierung der bestimmte Funktionen Beziehung zur benutzerdefinierten XML aus Microsoft Word entfernt wurde.  Diese Informationen bezüglich Microsoft Word dürfen nicht von Personen oder Organisationen in den Vereinigten Staaten oder ihren Außengebieten verwendet werden, die Programme verwenden oder entwickeln, die unter Microsoft Word\-Produkten ausgeführt werden, die von Microsoft nach dem 10. Januar 2010 lizenziert wurden. Diese Produkte verhalten sich nicht wie Produkte, die vor diesem Datum lizenziert oder für die Verwendung außerhalb der Vereinigten Staaten erworben und lizenziert wurden.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel und Microsoft Office Word ermöglichen es Ihnen, Dokumenten Schemas zuzuordnen.  Dieses Feature kann das Importieren und Exportieren von XML\-Daten in das Dokument bzw. aus dem Dokument erleichtern.  
  
 Visual Studio macht zugeordnete Schemaelemente als Steuerelemente im Programmiermodell in Anpassungen auf Dokumentebene verfügbar.  Excel wird durch Visual Studio um Unterstützung für das Binden von Steuerelementen an Daten in Datenbanken, Webdiensten und Objekten erweitert.  Word und Excel erhalten durch Visual Studio Unterstützung für Aktionsbereiche. Die Verwendung von Aktionsbereichen kann Ihren Projektmappen in Verbindung mit einem Dokument, das einem Schema zugeordnet wurde, mehr Benutzerfreundlichkeit verleihen.  Weitere Informationen finden Sie unter [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  In Excel\-Projektmappen können keine mehrteiligen XML\-Schemas verwendet werden.  
  
## Objekte, die beim Anfügen von Schemas an Excel\-Arbeitsmappen erstellt werden  
 Wenn Sie einer Arbeitsmappe ein Schema zuordnen, werden von Visual Studio automatisch einige Objekte erstellt und dem Projekt hinzugefügt.  Diese Objekte dürfen nicht mit Visual Studio\-Tools gelöscht werden, da sie von Excel verwaltet werden.  Entfernen Sie die zugeordneten Elemente aus dem Arbeitsblatt, oder trennen Sie das Schema mit Excel\-Tools ab, um die Objekte zu löschen.  
  
 Es gibt zwei Hauptobjekte:  
  
-   XML\-Schema \(XSD\-Datei\).  Für jedes Schema in der Arbeitsmappe fügt Visual Studio dem Projekt ein Schema hinzu.  Dieses wird im **Projektmappen\-Explorer** als Projektelement mit einer XSD\-Erweiterung angezeigt.  
  
-   Eine typisierte <xref:System.Data.DataSet>\-Klasse.  Diese Klasse wird auf Grundlage des Schemas erstellt.  Diese Dataset\-Klasse ist in der **Klassenansicht** sichtbar.  
  
## Objekte, die bei der Zuordnung von Schemaelementen zu Excel\-Arbeitsblättern erstellt werden  
 Wenn Sie einem Arbeitsblatt ein Schemaelement aus dem Aufgabenbereich **XML\-Quelle** zuordnen, werden von Visual Studio automatisch mehrere Objekte erstellt und dem Projekt hinzugefügt:  
  
-   Steuerelemente.  Für jedes zugeordnete Objekt in der Arbeitsmappe wird im Programmiermodell ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement \(für sich nicht wiederholende Schemaelemente\) oder ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement \(für sich wiederholende Schemaelemente\) erstellt.  Das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement kann nur gelöscht werden, indem die Zuordnungen und die zugeordneten Objekte aus der Arbeitsmappe gelöscht werden.  Weitere Informationen über Steuerelemente finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource.  Wenn Sie einen <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> durch Zuordnen eines sich nicht wiederholenden Schemaelements zum Arbeitsblatt erstellen, wird eine <xref:System.Windows.Forms.BindingSource> erzeugt und das <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement an die <xref:System.Windows.Forms.BindingSource> gebunden.  Sie müssen die <xref:System.Windows.Forms.BindingSource> an eine Instanz der Datenquelle binden, die mit dem Schema übereinstimmt, das dem Dokument zugeordnet wurde – also z. B. mit einer Instanz der typisierten <xref:System.Data.DataSet>\-Klasse, die erstellt wurde.  Erstellen Sie die Bindung, indem Sie im **Eigenschaftenfenster** die Eigenschaften <xref:System.Windows.Forms.BindingSource.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> festlegen.  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource> wird nicht für <xref:Microsoft.Office.Tools.Excel.ListObject>\-Objekte erstellt.  Sie müssen das <xref:Microsoft.Office.Tools.Excel.ListObject> durch Festlegen der Eigenschaften <xref:System.Windows.Forms.BindingSource.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> im **Eigenschaftenfenster** manuell an die Datenquelle binden.  
  
### Zugeordnete Schemas von Office und das Datenquellenfenster von Visual Studio  
 Sowohl mithilfe der zugeordneten Schemas von Office als auch über das **Datenquellenfenster** von Visual Studio können Sie Daten in einem Excel\-Arbeitsblatt zur Berichterstellung oder zur Bearbeitung präsentieren.  In beiden Fällen können Sie Datenelemente in das Excel\-Arbeitsblatt ziehen  Bei beiden Methoden werden Steuerelemente erstellt, die über eine <xref:System.Windows.Forms.BindingSource> an eine Datenquelle \(z. B. <xref:System.Data.DataSet>\) oder einen Webdienst an Daten gebunden sind.  
  
> [!NOTE]  
>  Wenn Sie einem Arbeitsblatt ein sich wiederholendes Schemaelement zuordnen, wird von Visual Studio <xref:Microsoft.Office.Tools.Excel.ListObject> erstellt.  Das <xref:Microsoft.Office.Tools.Excel.ListObject> wird durch die <xref:System.Windows.Forms.BindingSource> nicht automatisch an Daten gebunden.  Sie müssen das <xref:Microsoft.Office.Tools.Excel.ListObject> durch Festlegen der Eigenschaften <xref:System.Windows.Forms.BindingSource.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> im **Eigenschaftenfenster** manuell an die Datenquelle binden.  
  
 In der folgenden Tabelle werden einige der Unterschiede zwischen den beiden Methoden gezeigt.  
  
|XML\-Schema|Datenquellenfenster|  
|-----------------|-------------------------|  
|Verwendet die Office\-Schnittstelle.|Verwendet das **Datenquellenfenster** in Visual Studio.|  
|Aktiviert die integrierten Office\-Features für das Importieren und Exportieren von Daten in XML\-Dateien.|Sie müssen die Import\- und Exportfunktionalität programmgesteuert bereitstellen.|  
|Sie müssen Code schreiben, um die generierten Steuerelemente mit Daten zu füllen.|Für Steuerelemente, die Sie über das **Datenquellenfenster** hinzufügen, wird automatisch Code zum Füllen mit Daten generiert – einschließlich der benötigten Verbindungszeichenfolgen, wenn Sie Datenbankserver verwenden.|  
  
## Verhalten, wenn Schemas an Word\-Dokumente angefügt werden  
 Beim Anfügen eines Schemas an ein Word\-Dokument, das in einem Office\-Projekt auf Dokumentebene verwendet wird, werden keine Datenobjekte erstellt.  Es werden jedoch Steuerelemente erstellt, wenn Sie dem Dokument ein Schemaelement zuordnen.  Welche Art von Steuerelement erstellt wird, hängt von der Art des zugeordneten Elements ab. Bei wiederholenden Elementen werden <xref:Microsoft.Office.Tools.Word.XMLNodes>\-Steuerelemente generiert, während bei nicht wiederholenden Elementen <xref:Microsoft.Office.Tools.Word.XMLNode>\-Steuerelemente generiert werden.  Weitere Informationen finden Sie unter [XMLNodes-Steuerelement](../vsto/xmlnodes-control.md) und [XMLNode-Steuerelement](../vsto/xmlnode-control.md).  
  
## Bereitstellung von Projektmappen mit XML\-Schemas  
 Sie sollten einen Installer erstellen, um eine Projektmappe bereitzustellen, die ein XML\-Schema verwendet, das einem Dokument zugeordnet ist.  Der Installer sollte das Schema in der Schemabibliothek auf dem Computer des Benutzers registrieren.  Die Projektmappe funktioniert auch, wenn das Schema nicht registriert wird. In diesem Fall generiert Word nämlich beim Öffnen des Dokuments durch den Benutzer ein temporäres Schema, das auf den im Dokument enthaltenen Elementen basiert.  Das Schema, mit dem das Projekt erstellt wurde, kann jedoch vom Benutzer nicht gespeichert oder zum Validieren verwendet werden.  Weitere Informationen über Installer finden Sie unter [Bereitstellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md).  
  
 Sie können einem Projekt auch Code hinzufügen, durch den überprüft wird, ob sich das Schema in der Bibliothek befindet und registriert ist.  Wenn dies nicht der Fall ist, können Sie den Benutzer warnen.  
  
 [!code-csharp[Trin_VstcoreDataWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstcoreDataWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/VB/ThisDocument.vb#1)]  
  
## Siehe auch  
 [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  