---
title: "Exemplarische Vorgehensweise: Einlesen von XML-Daten in ein Dataset | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Lesen aus XML-Dateien"
  - "Datenzugriff [Visual Studio], XML-Daten"
  - "Datasets [Visual Basic], Lesen von XML-Daten"
  - "Lesen von Daten, XML-Dateien"
  - "Lesen von Dateien, XML"
  - "Lesen von XML"
  - "XML [Visual Studio], Lesen"
  - "XML-Dokumente, Lesen"
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Einlesen von XML-Daten in ein Dataset
ADO.NET stellt einfache Methoden für die Arbeit mit XML\-Daten bereit.  In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows\-Anwendung, durch die XML\-Daten in ein Dataset geladen werden.  Das Dataset wird anschließend in einer <xref:System.Windows.Forms.DataGridView> angezeigt.  Schließlich wird in einem Textfeld ein XML\-Schema angezeigt, das auf dem Inhalt der XML\-Datei basiert.  
  
 Diese exemplarische Vorgehensweise umfasst fünf Hauptschritte:  
  
1.  Erstellen eines neuen Projekts  
  
2.  Erstellen der in das Dataset einzulesenden XML\-Datei  
  
3.  Erstellen der Benutzeroberfläche  
  
4.  Erstellen des Datasets, Lesen der XML\-Datei und deren Anzeige in einem <xref:System.Windows.Forms.DataGridView>\-Steuerelement  
  
5.  Hinzufügen von Code zum Anzeigen des XML\-Schemas auf der Grundlage der XML\-Datei in einem <xref:System.Windows.Forms.TextBox>\-Steuerelement  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Erstellen eines neues Projekts  
 In diesem Schritt erstellen Sie ein Visual Basic\- oder ein Visual C\#\-Projekt, das auf dieser exemplarischen Vorgehensweise basiert.  
  
#### So erstellen Sie das neue Windows\-Projekt  
  
1.  Erstellen Sie über das Menü **Datei** ein neues Projekt.  
  
2.  Geben Sie dem Projekt den Namen `ReadingXML`.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **ReadingXML** wird erstellt und zum Projektmappen\-Explorer hinzugefügt.  
  
## Erstellen der in das Dataset einzulesenden XML\-Datei  
 Da diese exemplarische Vorgehensweise das Einlesen von XML\-Daten in ein Dataset behandelt, wird der Inhalt einer XML\-Datei bereitgestellt.  
  
#### So erstellen Sie die in das Dataset einzulesende XML\-Datei  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Wählen Sie **XML\-Datei** aus, nennen Sie die Datei `authors.xml`, und klicken Sie auf **Hinzufügen**.  
  
     Die XML\-Datei wird in den Designer geladen und steht zur Bearbeitung bereit.  
  
3.  Fügen Sie den folgenden Code in den Editor unter der XML\-Deklaration ein:  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4.  Zeigen Sie im Menü **Datei** auf **authors.xml speichern**.  
  
## Erstellen der Benutzeroberfläche  
 Die Benutzeroberfläche für diese Anwendung besteht aus folgenden Steuerelementen:  
  
-   Ein <xref:System.Windows.Forms.DataGridView>\-Steuerelement, das den Inhalt der XML\-Datei in Form von Daten anzeigt  
  
-   Ein <xref:System.Windows.Forms.TextBox>\-Steuerelement, das das XML\-Schema für die XML\-Datei anzeigt  
  
-   Zwei <xref:System.Windows.Forms.Button>\-Steuerelemente  
  
    -   Über eine Schaltfläche wird die XML\-Datei in das Dataset eingelesen und im <xref:System.Windows.Forms.DataGridView>\-Steuerelement angezeigt.  
  
    -   Mit einer zweiten Schaltfläche wird das Schema aus dem Dataset extrahiert und über einen <xref:System.IO.StringWriter> im <xref:System.Windows.Forms.TextBox>\-Steuerelement angezeigt.  
  
#### So fügen Sie dem Formular Steuerelemente hinzu  
  
1.  Öffnen Sie `Form1` in der Entwurfsansicht.  
  
2.  Ziehen Sie folgende Steuerelemente aus der **Toolbox** auf das Formular:  
  
    -   Ein <xref:System.Windows.Forms.DataGridView>\-Steuerelement  
  
    -   Ein <xref:System.Windows.Forms.TextBox>\-Steuerelement  
  
    -   Zwei <xref:System.Windows.Forms.Button>\-Steuerelemente  
  
3.  Legen Sie die folgenden Eigenschaften fest:  
  
    |Steuerelement|Property|Einstellung|  
    |-------------------|--------------|-----------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**Vertikal**|  
    |`Button1`|**Name**|`ReadXmlButton`|  
    ||**Text**|`XML lesen`|  
    |`Button2`|**Name**|`ShowSchemaButton`|  
    ||**Text**|`Schema anzeigen`|  
  
## Erstellen des Datasets, das die XML\-Daten empfängt  
 In dieser nächsten Prozedur wird das neue Dataset `authors` erstellt.  Weitere Informationen über Datasets finden Sie unter [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### So erstellen Sie ein neues Dataset, das die XML\-Daten empfängt  
  
1.  Wählen Sie in **Projektmappen\-Explorer** die Quelldatei für **Form1** aus, und klicken Sie auf der Symbolleiste **Projektmappen\-Explorer** auf die Schaltfläche **Ansicht\-Designer**.  
  
2.  Ziehen Sie ein **Dataset** aus der [Toolbox, Registerkarte "Daten"](../ide/reference/toolbox-data-tab.md) auf **Form1**.  
  
3.  Wählen Sie im Dialogfeld **DataSet hinzufügenNicht typisiertes DataSet** und klicken Sie dann auf **OK**.  
  
     **DataSet1** wird der Komponentenleiste hinzugefügt.  
  
4.  Legen Sie im **Eigenschaftenfenster** die **Name**\-Eigenschaft und die <xref:System.Data.DataSet.DataSetName%2A>\-Eigenschaft auf `AuthorsDataSet` fest.  
  
## Erstellen des Ereignishandlers zum Einlesen der XML\-Daten in das Dataset  
 Mit der Schaltfläche **XML lesen** wird die XML\-Datei in das Dataset eingelesen. Außerdem werden die Eigenschaften für das <xref:System.Windows.Forms.DataGridView>\-Steuerelement festgelegt, mit der die Bindung an das Dataset erstellt wird.  
  
#### So fügen Sie dem ReadXmlButton\_Click\-Ereignishandler Code hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** die Option **Form1** aus, und klicken Sie auf der Symbolleiste **Projektmappen\-Explorer** auf die Schaltfläche **Designer\-Ansicht**.  
  
2.  Doppelklicken Sie auf die Schaltfläche **XML lesen**.  
  
     Der **Code\-Editor** wird beim `ReadXmlButton_Click`\-Ereignishandler geöffnet.  
  
3.  Geben Sie den folgenden Code in den `ReadXmlButton_Click`\-Ereignishandler ein:  
  
     [!code-cs[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  Ändern Sie im `ReadXMLButton_Click`\-Ereignishandlercode den `filepath =`\-Eintrag in den richtigen Pfad.  
  
## Erstellen des Ereignishandlers zum Anzeigen des Schemas im Textfeld  
 Mit der Schaltfläche **Schema anzeigen** wird ein <xref:System.IO.StringWriter>\-Objekt erstellt, das mit dem Schema gefüllt und in <xref:System.Windows.Forms.TextBox> angezeigt wird.  
  
#### So fügen Sie dem ShowSchemaButton\_Click\-Ereignishandler Code hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** die Option **Form1** aus, und klicken Sie auf die Schaltfläche **Ansicht\-Designer**.  
  
2.  Doppelklicken Sie auf die Schaltfläche **Schema anzeigen**.  
  
     Der **Code\-Editor** wird beim `ShowSchemaButton_Click`\-Ereignishandler geöffnet.  
  
3.  Geben Sie den folgenden Code in den `ShowSchemaButton_Click`\-Ereignishandler ein.  
  
     [!code-cs[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## Testen  
 Sie können das Formular jetzt testen und prüfen, ob es sich wie wie erwartet verhält.  
  
#### So testen Sie das Formular  
  
1.  Drücken Sie F5, um die Anwendung auszuführen.  
  
2.  Klicken Sie auf die Schaltfläche **XML lesen**.  
  
     In der DataGridView wird der Inhalt der XML\-Datei angezeigt.  
  
3.  Klicken Sie auf die Schaltfläche **Schema anzeigen**.  
  
     Im Textfeld wird das XML\-Schema für die XML\-Datei angezeigt.  
  
## Nächste Schritte  
 Diese exemplarische Vorgehensweise behandelt die Grundlagen für das Einlesen einer XML\-Datei in ein Dataset sowie für das Erstellen eines Schemas, das auf dem Inhalt der XML\-Datei basiert.  Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Bearbeiten der Daten im Dataset und Zurückschreiben der Daten als XML.  Weitere Informationen finden Sie unter <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Bearbeiten der Daten im Dataset und Zurückschreiben der Daten in eine Datenbank.  Weitere Informationen finden Sie unter [Speichern von Daten](../data-tools/saving-data.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [XML\-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)