---
title: "Exemplarische Vorgehensweise: Binden von Inhaltssteuerelementen an benutzerdefinierte XML-Abschnitte"
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
  - "Inhaltssteuerelemente [Office-Entwicklung in Visual Studio], Datenbindung"
  - "Benutzerdefinierte XML-Teile, Binden an Inhaltssteuerelemente"
  - "Datenbindung [Office-Entwicklung in Visual Studio], Content-Steuerelemente"
  - "DatePickerContentControl, Binden an einen benutzerdefinierten XML-Teil"
  - "DropDownListContentControl, Binden von Elementen an einen benutzerdefinierten XML-Teil"
  - "PlainTextContentControl, Binden an einen benutzerdefinierten XML-Teil"
ms.assetid: 10d67769-6157-4703-a10c-d33e988f9095
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Exemplarische Vorgehensweise: Binden von Inhaltssteuerelementen an benutzerdefinierte XML-Abschnitte
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie Inhaltssteuerelemente in einer Anpassung auf Dokumentebene für Word an XML\-Daten binden, die in dem Dokument gespeichert sind.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Mit Word können Sie XML\-Daten, die als *benutzerdefinierte XML\-Abschnitte* bezeichnet werden, in einem Dokument speichern.  Sie können die Anzeige dieser Daten steuern, indem Sie Inhaltssteuerelemente an Elemente in einem benutzerdefinierten XML\-Abschnitt binden.  Im Beispieldokument dieser exemplarischen Vorgehensweise werden Mitarbeiterinformationen angezeigt, die in einem benutzerdefinierten XML\-Abschnitt gespeichert werden.  Wenn Sie das Dokument öffnen, zeigen die Inhaltssteuerelemente die Werte der XML\-Elemente an.  Am Text in den Inhaltssteuerelementen vorgenommene Änderungen werden im benutzerdefinierten XML\-Abschnitt gespeichert.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen von Inhaltssteuerelementen zum Word\-Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit.  
  
-   Erstellen einer XML\-Datendatei und eines XML\-Schemas, das die Elemente definiert, die an die Inhaltssteuerelemente gebunden werden sollen.  
  
-   Anfügen des XML\-Schemas an das Dokument zur Entwurfszeit.  
  
-   Hinzufügen des Inhalts der XML\-Datei zu einem benutzerdefinierten XML\-Abschnitt im Dokument zur Laufzeit.  
  
-   Binden der Inhaltssteuerelemente an Elemente im benutzerdefinierten XML\-Abschnitt.  
  
-   Binden eines <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an eine Gruppe von Werten, die im XML\-Schema definiert sind.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Erstellen eines neuen Word\-Dokumentprojekts  
 Erstellen Sie ein Word\-Dokument, das Sie in der exemplarischen Vorgehensweise verwenden.  
  
#### So erstellen Sie ein neues Word\-Dokumentprojekt  
  
1.  Erstellen Sie ein Word\-Dokumentprojekt mit dem Namen EmployeeControls.  Erstellen Sie ein neues Dokument für die Projektmappe.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet das neue Word\-Dokument im Designer und fügt dem **Projektmappen\-Explorer** das Projekt EmployeeControls hinzu.  
  
## Hinzufügen von Inhaltssteuerelementen zum Dokument  
 Erstellen Sie eine Tabelle, die drei verschiedene Typen von Inhaltssteuerelementen enthält, in der der Benutzer Informationen über einen Mitarbeiter anzeigen bzw. bearbeiten kann.  
  
#### So fügen Sie dem Dokument Inhaltssteuerelemente hinzu  
  
1.  Wählen Sie im Word\-Dokument, das im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Designer gehostet wird, auf dem Menüband die Registerkarte **Einfügen** aus.  
  
2.  Wählen Sie in der Gruppe **Tabellen** die Option **Tabelle**, und fügen Sie eine Tabelle mit 2 Spalten und 3 Zeilen ein.  
  
3.  Geben Sie in der ersten Spalte Text ein, sodass sie der folgenden Spalte ähnelt:  
  
    ||  
    |-|  
    |Employee Name|  
    |Hire Date|  
    |Titel|  
  
4.  Wählen Sie in der zweiten Spalte der Tabelle die erste Zeile \(neben **Employee Name**\).  
  
5.  Wählen Sie auf dem Menüband die Registerkarte **Entwickler**.  
  
    > [!NOTE]  
    >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf der Multifunktionsleiste](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  Wählen Sie in der Gruppe **Steuerelemente** die Schaltfläche **Text** mit der Bezeichnung ![PlainTextContentControl](../vsto/media/plaintextcontrol.png "PlainTextContentControl") aus, um der ersten Zelle ein <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> hinzuzufügen.  
  
7.  Wählen Sie in der zweiten Spalte der Tabelle die zweite Zeile \(neben **Hire Date**\).  
  
8.  Wählen Sie in der Gruppe **Steuerelemente** die Schaltfläche **Datumsauswahl** mit der Bezeichnung ![DatePickerContentControl](../vsto/media/datepicker.png "DatePickerContentControl") aus, um der zweiten Zelle ein <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> hinzuzufügen.  
  
9. Wählen Sie in der zweiten Spalte der Tabelle die dritte Zeile \(neben **Title**\).  
  
10. Wählen Sie in der Gruppe **Steuerelemente** die Schaltfläche **Dropdownliste** mit der Bezeichnung ![DropDownListContentControl](../vsto/media/dropdownlist.png "DropDownListContentControl") aus, um der letzten Zelle ein <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> hinzuzufügen.  
  
 Das ist die vollständige Benutzeroberfläche für dieses Projekt.  Wenn Sie das Projekt jetzt ausführen, können Sie in der ersten Zeile Text eingeben und in der zweiten Zeile ein Datum auswählen.  Im nächsten Schritt fügen Sie die anzuzeigenden Daten in einer XML\-Datei an das Dokument an.  
  
## Erstellen der XML\-Datendatei  
 Sie erhalten XML\-Daten zum Speichern in einem benutzerdefinierten XML\-Abschnitt üblicherweise von einer externen Quelle, wie etwa einer Datei oder Datenbank.  In dieser exemplarischen Vorgehensweise erstellen Sie eine XML\-Datei mit Mitarbeiterdaten, die durch Elemente gekennzeichnet sind, die Sie an die Inhaltssteuerelemente im Dokument binden.  Um die Daten zur Laufzeit verfügbar zu machen, betten Sie die XML\-Datei als Ressource in die Anpassungsassembly.  
  
#### So erstellen Sie die Datendatei  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  Wählen Sie im Bereich **Vorlagen** die Option **XML\-Datei** aus.  
  
3.  Nennen Sie die Datei **employees.xml**, und klicken Sie dann auf die Schaltfläche **Hinzufügen**.  
  
     Die Datei **employees.xml** wird im Code\-Editor geöffnet.  
  
4.  Ersetzen Sie den Inhalt der Datei **employees.xml** durch den folgenden Text:  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  Wählen Sie im **Projektmappen\-Explorer** die Datei **employees.xml** aus.  
  
6.  Wählen Sie im **Eigenschaftenfenster** die **Build Action**\-Eigenschaft aus, und ändern Sie dann den Wert in **Eingebettete Ressource**.  
  
     Dieser Schritt bettet die XML\-Datei als Ressource in die Assembly ein, wenn Sie das Projekt erstellen.  Dadurch können Sie auf den Inhalt der XML\-Datei zur Laufzeit zugreifen.  
  
## Erstellen eines XML\-Schemas  
 Wenn Sie ein Inhaltssteuerelement an ein einzelnes Element in einem benutzerdefinierten XML\-Abschnitt binden möchten, müssen Sie kein XML\-Schema verwenden.  Um jedoch das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an einen Satz von Werten zu binden, müssen Sie ein XML\-Schema erstellen, das die zuvor erstellte XML\-Datendatei überprüft.  Das XML\-Schema definiert die möglichen Werte für das `title`\-Element.  Im weiteren Verlauf dieser exemplarischen Vorgehensweise binden Sie das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an dieses Element.  
  
#### So erstellen Sie ein XML\-Schema  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  Wählen Sie im Bereich **Vorlagen** die Option **XML\-Schema** aus.  
  
3.  Nennen Sie das Schema **employees.xsd**, und wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
     Der Schema\-Designer wird geöffnet.  
  
4.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für **employees.xsd**, und wählen Sie **Code anzeigen** aus.  
  
5.  Ersetzen Sie den Inhalt der Datei **employees.xsd** durch das folgende Schema.  
  
    ```  
  
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"   
        targetNamespace="http://schemas.microsoft.com/vsto/samples"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema"  
        elementFormDefault="qualified">  
      <xs:element name="employees" type="EmployeesType"></xs:element>  
      <xs:complexType name="EmployeesType">  
        <xs:all>  
          <xs:element name="employee" type="EmployeeType"/>  
        </xs:all>  
      </xs:complexType>  
      <xs:complexType name="EmployeeType">  
        <xs:sequence>  
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:simpleType name="TitleType">  
        <xs:restriction base="xs:string">  
          <xs:enumeration value ="Engineer"/>  
          <xs:enumeration value ="Designer"/>  
          <xs:enumeration value ="Manager"/>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:schema>  
    ```  
  
6.  Klicken Sie im Menü **Datei** auf **Alle speichern**, um die Änderungen an den Dateien **employees.xml** und **employees.xsd** zu speichern.  
  
## Anfügen des XML\-Schemas an das Dokument  
 Sie müssen das XML\-Schema an das Dokument anfügen, um das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an die gültigen Werte des `title`\-Elements zu binden.  
  
#### So fügen Sie das XML\-Schema an das Dokument an \([!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]\)  
  
1.  Aktivieren Sie **EmployeeControls.docx** im Designer.  
  
2.  Wählen Sie auf dem Menüband die Registerkarte **Entwickler** aus, und wählen Sie dann die Schaltfläche **Add\-Ins** aus.  
  
3.  Wählen Sie das Dialogfeld **Vorlagen und Add\-Ins**, dann die Registerkarte **XML\-Schema** und anschließend die Schaltfläche **Schema hinzufügen**.  
  
4.  Wechseln Sie zum zuvor erstellten Schema **employees.xsd**, das sich im Projektverzeichnis befindet, und wählen Sie dann die Schaltfläche **Öffnen**.  
  
5.  Wählen Sie im Dialogfeld **Schemaeinstellungen** die Schaltfläche **OK**.  
  
6.  Wählen Sie die Schaltfläche **OK**, um das Dialogfeld **Vorlagen und Add\-Ins** zu schließen.  
  
#### So fügen Sie das XML\-Schema an das Dokument an \(Word 2010\)  
  
1.  Aktivieren Sie **EmployeeControls.docx** im Designer.  
  
2.  Wählen Sie auf dem Menüband die Registerkarte **Entwickler**.  
  
3.  Wählen Sie in der Gruppe **XML** die Schaltfläche **Schema** aus.  
  
4.  Wählen Sie das Dialogfeld **Vorlagen und Add\-Ins**, dann die Registerkarte **XML\-Schema** und anschließend die Schaltfläche **Schema hinzufügen**.  
  
5.  Wechseln Sie zum zuvor erstellten Schema **employees.xsd**, das sich im Projektverzeichnis befindet, und wählen Sie dann die Schaltfläche **Öffnen**.  
  
6.  Wählen Sie im Dialogfeld **Schemaeinstellungen** die Schaltfläche **OK**.  
  
7.  Wählen Sie die Schaltfläche **OK**, um das Dialogfeld **Vorlagen und Add\-Ins** zu schließen.  
  
     Der Aufgabenbereich **XML\-Struktur** wird geöffnet.  
  
8.  Schließen Sie den **XML\-Struktur**\-Aufgabenbereich.  
  
## Hinzufügen eines benutzerdefinierten XML\-Abschnitts zum Dokument  
 Bevor Sie die Inhaltssteuerelemente an die Elemente in der XML\-Datei binden können, müssen Sie einem neuen benutzerdefiniertem XML\-Abschnitt im Dokument den Inhalt der XML\-Datei hinzufügen.  
  
#### So fügen Sie dem Dokument einen benutzerdefinierten XML\-Abschnitt hinzu  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für **ThisDocument.cs** oder **ThisDocument.vb**, und wählen Sie dann **Code anzeigen** aus.  
  
2.  Fügen Sie der `ThisDocument`\-Klasse die folgenden Deklarationen hinzu.  In diesem Code werden mehrere Objekte deklariert, mit denen Sie dem Dokument einen benutzerdefinierten XML\-Abschnitt hinzufügen.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  Fügen Sie der `ThisDocument`\-Klasse die folgende Methode hinzu.  Diese Methode ruft den Inhalt der XML\-Datendatei ab, die als Ressource in der Assembly eingebettet ist, und gibt den Inhalt als XML\-Zeichenfolge zurück.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#3)]  
  
4.  Fügen Sie der `ThisDocument`\-Klasse die folgende Methode hinzu.  Die `AddCustomXmlPart`\-Methode erstellt einen neuen benutzerdefinierten XML\-Abschnitt, der eine XML\-Zeichenfolge enthält, die an die Methode übergeben wird.  
  
     Um sicherzustellen, dass der benutzerdefinierte XML\-Abschnitt nur einmal erstellt wird, erstellt die Methode den benutzerdefinierten XML\-Abschnitt nur dann, wenn noch kein benutzerdefinierter XML\-Abschnitt mit einer übereinstimmenden GUID im Dokument vorhanden ist.  Beim ersten Aufruf dieser Methode wird der Wert der <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A>\-Eigenschaft in der Zeichenfolge `employeeXMLPartID` gespeichert.  Der Wert der `employeeXMLPartID`\-Zeichenfolge wird im Dokument beibehalten, da er mit dem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>\-Attribut deklariert wurde.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#4)]  
  
## Binden der Inhaltssteuerelemente an Elemente im benutzerdefinierten XML\-Abschnitt  
 Binden Sie mit der **XMLMapping**\-Eigenschaft des jeweiligen Inhaltssteuerelements jedes Inhaltssteuerelement an ein Element im benutzerdefinierten XML\-Abschnitt.  
  
#### So binden Sie die Inhaltssteuerelemente an Elemente im benutzerdefinierten XML\-Abschnitt  
  
1.  Fügen Sie der `ThisDocument`\-Klasse die folgende Methode hinzu.  Mit dieser Methode wird jedes Inhaltssteuerelement an ein Element im benutzerdefinierten XML\-Abschnitt gebunden und die Anzeige des Datumsformats für das <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> festgelegt.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#5)]  
  
## Ausführen des Codes beim Öffnen des Dokuments  
 Erstellen Sie den benutzerdefinierten XML\-Abschnitt, und binden Sie die benutzerdefinierten Steuerelemente an die Daten, wenn das Dokument geöffnet wird.  
  
#### So führen Sie den Code beim Öffnen des Dokuments aus  
  
1.  Fügen Sie der `ThisDocument_Startup`\-Methode der `ThisDocument`\-Klasse den folgenden Code hinzu.  Mit diesem Code wird die XML\-Zeichenfolge aus der Datei **employees.xml** abgerufen, die XML\-Zeichenfolge einem neuen benutzerdefinierten XML\-Abschnitt im Dokument hinzugefügt, und die Inhaltssteuerelemente werden an Elemente im benutzerdefinierten XML\-Abschnitt gebunden.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#2)]  
  
## Testen des Projekts  
 Wenn Sie das Dokument öffnen, zeigen die Inhaltssteuerelemente Daten der Elemente im benutzerdefinierten XML\-Abschnitt an.  Sie können auf das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> klicken, um einen von drei gültigen Werten, die in der Datei **employees.xsd** definiert werden, für das `title`\-Element auszuwählen.  Wenn Sie die Daten in einem Inhaltssteuerelement bearbeiten, werden die neuen Werte im benutzerdefinierten XML\-Abschnitt im Dokument gespeichert.  
  
#### So testen Sie die Inhaltssteuerelemente  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Überprüfen Sie, ob die Tabelle im Dokument ähnlich aussieht wie die folgende Tabelle.  Jede der Zeichenfolgen in der zweiten Spalte wird von einem Element im benutzerdefinierten XML\-Abschnitt im Dokument abgerufen.  
  
    |||  
    |-|-|  
    |Employee Name|**Karina Leal**|  
    |Hire Date|**April 1, 1999**|  
    |Titel|**Manager**|  
  
3.  Wählen Sie die Zelle rechts neben der Zelle "Employee Name", und geben Sie einen anderen Namen ein.  
  
4.  Wählen Sie die Zelle rechts neben der Zelle "Hire Date", und wählen Sie in der Datumsauswahl ein anderes Datum aus.  
  
5.  Wählen Sie die Zelle rechts neben der Zelle "Title", und wählen Sie ein neues Element aus der Dropdownliste aus.  
  
6.  Speichern und schließen Sie das Dokument.  
  
7.  Öffnen Sie im Datei\-Explorer den Ordner "\\bin\\Debug" unter dem Speicherort des Projekts.  
  
8.  Öffnen Sie das Kontextmenü für "EmployeeControls.docx", und wählen Sie dann **Umbenennen** aus.  
  
9. Nennen Sie die Datei EmployeeControls.docx.zip.  
  
     Das Dokument EmployeeControls.docx wird im Open XML\-Format gespeichert.  Durch Umbenennen dieses Dokuments mit der ZIP\-Dateinamenserweiterung können Sie den Inhalt des Dokuments überprüfen.  Weitere Informationen zu Open XML finden Sie im technischen Artikel [Einführung in die Microsoft Office \(2007\) Open XML\-Dateiformate](http://msdn.microsoft.com/de-de/96018532-f62c-4da7-bbff-16b96a483fbf).  
  
10. Öffnen Sie die Datei "EmployeeControls.docx.zip".  
  
11. Öffnen Sie den Ordner **customXml**.  
  
12. Öffnen Sie das Kontextmenü für **item2.xml**, und wählen Sie dann **Öffnen** aus.  
  
     Diese Datei enthält den benutzerdefinierten XML\-Abschnitt, den Sie dem Dokument hinzugefügt haben.  
  
13. Überprüfen Sie, ob die Elemente `name`, `hireDate` und `title` die neuen Werte enthalten, die Sie in die Inhaltssteuerelemente im Dokument eingegeben haben.  
  
14. Schließen Sie die Datei **item2.xml**.  
  
## Nächste Schritte  
 Weitere Informationen über die Verwendung von Inhaltssteuerelementen finden Sie in den folgenden Themen:  
  
-   Erstellen Sie eine Vorlage mithilfe aller verfügbaren Inhaltssteuerelemente.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Vorlage mithilfe von Inhaltssteuerelementen](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Ändern Sie die Daten in den benutzerdefinierten XML\-Abschnitten bei geschlossenem Dokument.  Wenn der Benutzer das Dokument das nächste Mal öffnet, zeigen die Inhaltssteuerelemente, die an die XML\-Elemente gebunden sind, die neuen Daten an.  
  
-   Schützen Sie Teile eines Dokuments mithilfe von Inhaltssteuerelementen.  Weitere Informationen finden Sie unter [Gewusst wie: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## Siehe auch  
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Inhaltssteuerelemente](../vsto/content-controls.md)   
 [Gewusst wie: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Gewusst wie: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  