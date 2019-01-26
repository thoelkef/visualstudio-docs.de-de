---
title: 'Exemplarische Vorgehensweise: Binden von Inhaltssteuerelementen an benutzerdefinierte XML-Abschnitte'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 123282862f8ab6e7400f14a1aa07942885257e17
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864734"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Exemplarische Vorgehensweise: Binden von Inhaltssteuerelementen an benutzerdefinierte XML-Abschnitte
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie Inhaltssteuerelemente in einer Anpassung auf Dokumentebene für Word an XML-Daten binden, die in dem Dokument gespeichert sind.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word können Sie zum Speichern von XML-Daten, mit dem Namen *benutzerdefinierte XML-Elemente*, in einem Dokument. Sie können die Anzeige dieser Daten steuern, indem Sie Inhaltssteuerelemente an Elemente in einem benutzerdefinierten XML-Abschnitt binden. Im Beispieldokument dieser exemplarischen Vorgehensweise werden Mitarbeiterinformationen angezeigt, die in einem benutzerdefinierten XML-Abschnitt gespeichert werden. Wenn Sie das Dokument öffnen, zeigen die Inhaltssteuerelemente die Werte der XML-Elemente an. Am Text in den Inhaltssteuerelementen vorgenommene Änderungen werden im benutzerdefinierten XML-Abschnitt gespeichert.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
- Hinzufügen von Inhaltssteuerelementen zum Word-Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit.  
  
- Erstellen einer XML-Datendatei und eines XML-Schemas, das die Elemente definiert, die an die Inhaltssteuerelemente gebunden werden sollen.  
  
- Anfügen des XML-Schemas an das Dokument zur Entwurfszeit.  
  
- Hinzufügen von den Inhalt der XML-Datei an einen benutzerdefinierten XML-Abschnitt im Dokument zur Laufzeit.  
  
- Binden der Inhaltssteuerelemente an Elemente im benutzerdefinierten XML-Abschnitt.  
  
- Binden eines <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an eine Gruppe von Werten, die im XML-Schema definiert sind.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-a-new-word-document-project"></a>Erstellen Sie ein neues Word-Dokumentprojekt  
 Erstellen Sie ein Word-Dokument, das Sie in der exemplarischen Vorgehensweise verwenden.  
  
### <a name="to-create-a-new-word-document-project"></a>So erstellen Sie ein neues Word-Dokumentprojekt  
  
1.  Erstellen Sie ein Word-Dokumentprojekt mit dem Namen **EmployeeControls**. Erstellen Sie ein neues Dokument für die Projektmappe. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Öffnet das neue Word-Dokument im Designer und fügt die **EmployeeControls** Projekt **Projektmappen-Explorer**.  
  
## <a name="add-content-controls-to-the-document"></a>Hinzufügen von Inhaltssteuerelementen zum Dokument  
 Erstellen Sie eine Tabelle, die drei verschiedene Typen von Inhaltssteuerelementen enthält, in der der Benutzer Informationen über einen Mitarbeiter anzeigen bzw. bearbeiten kann.  
  
### <a name="to-add-content-controls-to-the-document"></a>So fügen Sie dem Dokument Inhaltssteuerelemente hinzu  
  
1. Im Word-Dokument, das im gehostet ist die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wählen Sie auf dem Menüband-Designer die **einfügen** Registerkarte.  
  
2. In der **Tabellen** Gruppe **Tabelle**, und fügen Sie eine Tabelle mit 2 Spalten und 3 Zeilen.  
  
3. Geben Sie in der ersten Spalte Text ein, sodass sie der folgenden Spalte ähnelt:  
  
   ||  
   |-|  
   |**Name des Mitarbeiters**|  
   |**Einstellungsdatum**|  
   |**Titel**|  
  
4. Wählen Sie in der zweiten Spalte der Tabelle, die erste Zeile (neben **Mitarbeiternamen**).  
  
5. Wählen Sie auf dem Menüband der **Developer** Registerkarte.  
  
   > [!NOTE]  
   >  Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. In der **Steuerelemente** Gruppe der **Text** Schaltfläche ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") Hinzufügen einer <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>bis zur ersten Zelle.  
  
7. Wählen Sie in der zweiten Spalte der Tabelle, die zweite Zeile (neben **Hire Date**).  
  
8. In der **Steuerelemente** Gruppe der **Datumsauswahl** Schaltfläche ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") eine Hinzufügen<xref:Microsoft.Office.Tools.Word.DatePickerContentControl> der zweiten Zelle.  
  
9. Wählen Sie in der zweiten Spalte der Tabelle, die dritte Zeile (neben **Titel**).  
  
10. In der **Steuerelemente** Gruppe der **Dropdown-Listenfeld** Schaltfläche ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") hinzufügen eine <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> bis zur letzten Zelle.  
  
    Das ist die vollständige Benutzeroberfläche für dieses Projekt. Wenn Sie das Projekt jetzt ausführen, können Sie in der ersten Zeile Text eingeben und in der zweiten Zeile ein Datum auswählen. Im nächsten Schritt fügen Sie die anzuzeigenden Daten in einer XML-Datei an das Dokument an.  
  
## <a name="create-the-xml-data-file"></a>Erstellen Sie die XML-Datendatei  
 Sie erhalten XML-Daten zum Speichern in einem benutzerdefinierten XML-Abschnitt üblicherweise von einer externen Quelle, wie etwa einer Datei oder Datenbank. In dieser exemplarischen Vorgehensweise erstellen Sie eine XML-Datei mit Mitarbeiterdaten, die durch Elemente gekennzeichnet sind, die Sie an die Inhaltssteuerelemente im Dokument binden. Um die Daten zur Laufzeit verfügbar zu machen, betten Sie die XML-Datei als Ressource in die Anpassungsassembly.  
  
#### <a name="to-create-the-data-file"></a>So erstellen Sie die Datendatei  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  In der **Vorlagen** wählen Sie im Bereich **XML-Datei**.  
  
3.  Nennen Sie die Datei **employees.xml**, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die **employees.xml** Datei wird im Code-Editor geöffnet.  
  
4.  Ersetzen Sie den Inhalt von der **employees.xml** -Datei mit den folgenden Text.  
  
    ```xml 
    <?xml version="1.0" encoding="utf-8" ?>  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  In **Projektmappen-Explorer**, wählen Sie die **employees.xml** Datei.  
  
6.  In der **Eigenschaften** wählen Sie im Fenster der **Buildvorgang** -Eigenschaft, und ändern Sie den Wert auf **eingebettete Ressource**.  
  
     Dieser Schritt bettet die XML-Datei als Ressource in die Assembly ein, wenn Sie das Projekt erstellen. Dadurch können Sie Zugriff auf den Inhalt der XML-Datei zur Laufzeit.  
  
## <a name="create-an-xml-schema"></a>Erstellen eines XML-Schemas  
 Wenn Sie ein Inhaltssteuerelement an ein einzelnes Element in einem benutzerdefinierten XML-Abschnitt binden möchten, müssen Sie kein XML-Schema verwenden. Um jedoch das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an einen Satz von Werten zu binden, müssen Sie ein XML-Schema erstellen, das die zuvor erstellte XML-Datendatei überprüft. Das XML-Schema definiert die möglichen Werte für das `title`-Element. Im weiteren Verlauf dieser exemplarischen Vorgehensweise binden Sie das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an dieses Element.  
  
#### <a name="to-create-an-xml-schema"></a>So erstellen Sie ein XML-Schema  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
2.  In der **Vorlagen** wählen Sie im Bereich **XML-Schema**.  
  
3.  Geben Sie dem Schema **employees.xsd** , und wählen Sie die **hinzufügen** Schaltfläche.  
  
     Der Schema-Designer wird geöffnet.  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **employees.xsd**, und wählen Sie dann **Ansichtscode**.  
  
5.  Ersetzen Sie den Inhalt von der **employees.xsd** Datei mit dem folgenden Schema.  
  
    ```xml
    <?xml version="1.0" encoding="utf-8" ?>  
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
  
6.  Auf der **Datei** Menü klicken Sie auf **alle speichern** zum Speichern der Änderungen auf die **employees.xml** und **employees.xsd** Dateien.  
  
## <a name="attach-the-xml-schema-to-the-document"></a>Fügen Sie das XML-Schema an das Dokument  
 Sie müssen das XML-Schema an das Dokument anfügen, um das <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> an die gültigen Werte des `title`-Elements zu binden.  
  
### <a name="to-attach-the-xml-schema-to-the-document--includeword15shortvstoincludesword-15-short-mdmd"></a>Das XML-Schema an das Dokument an ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])  
  
1.  Aktivieren Sie **EmployeeControls.docx** im Designer.  
  
2.  Wählen Sie auf dem Menüband der **Developer** Registerkarte, und wählen Sie dann die **-Add-Ins** Schaltfläche.  
  
3.  In der **Vorlagen und Add-Ins** Dialogfeld auf die **XML-Schema** Registerkarte, und wählen Sie dann die **Schema hinzufügen** Schaltfläche.  
  
4.  Navigieren Sie zu der **employees.xsd** Schema Sie zuvor erstellt haben, die im Projektverzeichnis befindet, und wählen Sie dann die **öffnen** Schaltfläche.  
  
5.  Wählen Sie die **OK** Schaltfläche der **Schema Einstellungen** Dialogfeld.  
  
6.  Wählen Sie die **OK** Schaltfläche zum Schließen der **Vorlagen und Add-Ins** Dialogfeld.  
  
### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>So fügen Sie das XML-Schema an das Dokument an (Word 2010)  
  
1.  Aktivieren Sie **EmployeeControls.docx** im Designer.  
  
2.  Wählen Sie auf dem Menüband der **Developer** Registerkarte.  
  
3.  In der **XML** Gruppe der **Schema** Schaltfläche.  
  
4.  In der **Vorlagen und Add-Ins** Dialogfeld auf die **XML-Schema** Registerkarte, und wählen Sie dann die **Schema hinzufügen** Schaltfläche.  
  
5.  Navigieren Sie zu der **employees.xsd** Schema, die Sie zuvor erstellt haben, befindet sich in Ihrem Projektverzeichnis, und wählen Sie die **öffnen** Schaltfläche.  
  
6.  Wählen Sie die **OK** Schaltfläche der **Schema Einstellungen** Dialogfeld.  
  
7.  Wählen Sie die **OK** Schaltfläche zum Schließen der **Vorlagen und Add-Ins** Dialogfeld.  
  
     Die **XML-Struktur** Aufgabe wird geöffnet.  
  
8.  Schließen der **XML-Struktur** Aufgabenbereich.  
  
## <a name="add-a-custom-xml-part-to-the-document"></a>Fügen Sie ein benutzerdefiniertes XML-Element zum Dokument  
 Bevor Sie die Inhaltssteuerelemente an die Elemente in der XML-Datei binden können, müssen Sie einem neuen benutzerdefiniertem XML-Abschnitt im Dokument den Inhalt der XML-Datei hinzufügen.  
  
### <a name="to-add-a-custom-xml-part-to-the-document"></a>So fügen Sie dem Dokument einen benutzerdefinierten XML-Abschnitt hinzu  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **ThisDocument.cs** oder **ThisDocument.vb**, und wählen Sie dann **Ansichtscode**.  
  
2.  Fügen Sie der `ThisDocument`-Klasse die folgenden Deklarationen hinzu. In diesem Code werden mehrere Objekte deklariert, mit denen Sie dem Dokument einen benutzerdefinierten XML-Abschnitt hinzufügen.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]  
  
3.  Fügen Sie der `ThisDocument` -Klasse die folgende Methode hinzu. Diese Methode ruft den Inhalt der XML-Datendatei ab, die als Ressource in der Assembly eingebettet ist, und gibt den Inhalt als XML-Zeichenfolge zurück.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]  
  
4.  Fügen Sie der `ThisDocument` -Klasse die folgende Methode hinzu. Die `AddCustomXmlPart`-Methode erstellt einen neuen benutzerdefinierten XML-Abschnitt, der eine XML-Zeichenfolge enthält, die an die Methode übergeben wird.  
  
     Um sicherzustellen, dass der benutzerdefinierte XML-Abschnitt nur einmal erstellt wird, erstellt die Methode den benutzerdefinierten XML-Abschnitt nur dann, wenn noch kein benutzerdefinierter XML-Abschnitt mit einer übereinstimmenden GUID im Dokument vorhanden ist. Beim ersten Aufruf dieser Methode wird der Wert der <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A>-Eigenschaft in der Zeichenfolge `employeeXMLPartID` gespeichert. Der Wert der `employeeXMLPartID`-Zeichenfolge wird im Dokument beibehalten, da er mit dem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>-Attribut deklariert wurde.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]  
  
## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Binden der Inhaltssteuerelemente an Elemente im benutzerdefinierten XML-Element  
 Jedes Inhaltssteuerelement an ein Element im benutzerdefinierten XML-Abschnitt binden, indem die **XMLMapping** Eigenschaft des jeweiligen Inhaltssteuerelements.  
  
### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>So binden Sie die Inhaltssteuerelemente an Elemente im benutzerdefinierten XML-Abschnitt  
  
1.  Fügen Sie der `ThisDocument` -Klasse die folgende Methode hinzu. Mit dieser Methode wird jedes Inhaltssteuerelement an ein Element im benutzerdefinierten XML-Abschnitt gebunden und die Anzeige des Datumsformats für das <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> festgelegt.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]  
  
## <a name="run-your-code-when-the-document-is-opened"></a>Führen Sie den Code ein, wenn das Dokument geöffnet ist  
 Erstellen Sie den benutzerdefinierten XML-Abschnitt, und binden Sie die benutzerdefinierten Steuerelemente an die Daten, wenn das Dokument geöffnet wird.  
  
### <a name="to-run-your-code-when-the-document-is-opened"></a>So führen Sie den Code beim Öffnen des Dokuments aus  
  
1.  Fügen Sie der `ThisDocument_Startup`-Methode der `ThisDocument`-Klasse den folgenden Code hinzu. Dieser Code Ruft die XML-Zeichenfolge aus der **employees.xml** -Datei, die XML-Zeichenfolge, einem neuen benutzerdefinierten XML-Abschnitt im Dokument hinzugefügt, und die Inhaltssteuerelemente an Elemente im benutzerdefinierten XML-Abschnitt gebunden.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]  
  
## <a name="test-the-project"></a>Testen Sie das Projekt  
 Wenn Sie das Dokument öffnen, zeigen die Inhaltssteuerelemente Daten der Elemente im benutzerdefinierten XML-Abschnitt an. Klicken Sie auf die <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> zum Auswählen eines drei gültigen Werte für die `title` -Element, das in definierten die **employees.xsd** Datei. Wenn Sie die Daten in einem Inhaltssteuerelement bearbeiten, werden die neuen Werte im benutzerdefinierten XML-Abschnitt im Dokument gespeichert.  
  
### <a name="to-test-the-content-controls"></a>So testen Sie die Inhaltssteuerelemente  
  
1.  Drücken Sie **F5**, um das Projekt auszuführen.  
  
2.  Überprüfen Sie, ob die Tabelle im Dokument ähnlich aussieht wie die folgende Tabelle. Jede der Zeichenfolgen in der zweiten Spalte wird von einem Element im benutzerdefinierten XML-Abschnitt im Dokument abgerufen.  
  
    |||  
    |-|-|  
    |**Name des Mitarbeiters**|**Karina Leal**|  
    |**Einstellungsdatum**|**Ab dem 1. April 1999**|  
    |**Titel**|**Manager**|  
  
3.  Wählen Sie die Zelle rechts neben der **Mitarbeiternamen** Zelle und geben Sie einen anderen Namen.  
  
4.  Wählen Sie die Zelle rechts neben der **Hire Date** Zelle, und wählen Sie in der Datumsauswahl ein anderes Datum aus.  
  
5.  Wählen Sie die Zelle rechts neben der **Titel** Zelle, und wählen Sie ein neues Element aus der Dropdown-Liste.  
  
6.  Speichern und schließen Sie das Dokument.  
  
7.  Öffnen Sie im Datei-Explorer die *\bin\Debug* Ordner unter dem Speicherort des Projekts.  
  
8.  Öffnen Sie das Kontextmenü für **EmployeeControls.docx** und wählen Sie dann **umbenennen**.  
  
9. Nennen Sie die Datei **EmployeeControls.docx.zip**.  
  
     Die **EmployeeControls.docx** Dokument im Open XML-Format gespeichert. Durch Umbenennen dieses Dokuments mit der *ZIP* Dateinamenerweiterung, Sie können den Inhalt des Dokuments überprüfen. Weitere Informationen zu Open XML finden Sie im technischen Artikel [Einführung in die Office (2007) Open XML-Dateiformate](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).  
  
10. Öffnen der **EmployeeControls.docx.zip** Datei.  
  
11. Öffnen der **CustomXml** Ordner.  
  
12. Öffnen Sie das Kontextmenü für **item2.xml** und wählen Sie dann **öffnen**.  
  
     Diese Datei enthält den benutzerdefinierten XML-Abschnitt, den Sie dem Dokument hinzugefügt haben.  
  
13. Überprüfen Sie, ob die Elemente `name`, `hireDate` und `title` die neuen Werte enthalten, die Sie in die Inhaltssteuerelemente im Dokument eingegeben haben.  
  
14. Schließen der **item2.xml** Datei.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Weitere Informationen über die Verwendung von Inhaltssteuerelementen finden Sie in den folgenden Themen:  
  
-   Erstellen Sie eine Vorlage mithilfe aller verfügbaren Inhaltssteuerelemente. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen Sie eine Vorlage mithilfe von Inhaltssteuerelementen](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Ändern Sie die Daten in den benutzerdefinierten XML-Abschnitten bei geschlossenem Dokument. Wenn der Benutzer das Dokument das nächste Mal öffnet, zeigen die Inhaltssteuerelemente, die an die XML-Elemente gebunden sind, die neuen Daten an.  
  
-   Schützen Sie Teile eines Dokuments mithilfe von Inhaltssteuerelementen. Weitere Informationen finden Sie unter [Vorgehensweise: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [ContentControl-Elemente](../vsto/content-controls.md)   
 [Vorgehensweise: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Vorgehensweise: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)  
