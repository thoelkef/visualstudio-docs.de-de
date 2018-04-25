---
title: Lesen von XML-Daten in ein dataset
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c6c2ea2b46fcd05360e079dc84da9bfe807ff489
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="read-xml-data-into-a-dataset"></a>Lesen von XML-Daten in ein dataset
ADO.NET stellt einfache Methoden zum Arbeiten mit XML-Daten bereit. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows-Anwendung, die XML-Daten in ein Dataset lädt. Das Dataset wird dann angezeigt, einem <xref:System.Windows.Forms.DataGridView> Steuerelement. Schließlich wird ein XML-Schema basierend auf dem Inhalt der XML-Datei in einem Textfeld angezeigt.

 In dieser exemplarischen Vorgehensweise besteht aus fünf wichtigen Schritte durchführen:

1.  Erstellen eines neuen Projekts

2.  Erstellen eine XML-Datei in das Dataset gelesen werden

3.  Erstellen der Benutzeroberfläche

4.  Erstellen des Datasets, die XML-Datei lesen und anzeigen in einem <xref:System.Windows.Forms.DataGridView> Steuerelement

5.  Hinzufügen von Code zum Anzeigen des XML-Schemas basierend auf der XML-Datei in einem <xref:System.Windows.Forms.TextBox> Steuerelement

> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle angezeigten Menübefehle je nach Ihren aktiven Einstellungen oder der Ausgabe in der Hilfe beschriebenen abweichen kann, verwendet wird. So ändern Sie die Einstellungen für die **Tools** klicken Sie im Menü **Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt
 In diesem Schritt erstellen Sie ein Visual Basic- oder Visual C#-Projekt, in dieser exemplarischen Vorgehensweise enthält.

#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt

1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **ReadingXML**, und wählen Sie dann **OK**.

     Die **ReadingXML** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generieren der XML-Datei in das Dataset gelesen werden
 Da in dieser exemplarischen Vorgehensweise konzentriert sich auf das Lesen von XML-Daten in ein Dataset, wird der Inhalt einer XML-Datei bereitgestellt.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Um die XML-Datei zu erstellen, die in das Dataset gelesen werden

1.  Auf der **Projekt** klicken Sie im Menü **neues Element hinzufügen**.

2.  Wählen Sie **XML-Datei**, nennen Sie die Datei `authors.xml`, und wählen Sie dann **hinzufügen**.

     Die XML-Datei in den Designer geladen und ist zur Bearbeitung bereit.

3.  Fügen Sie den folgenden Code in den Editor unter der XML-Deklaration:

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

4.  Auf der **Datei** klicken Sie im Menü **authors.xml speichern**.

## <a name="create-the-user-interface"></a>Erstellen der Benutzeroberfläche
 Die Benutzeroberfläche für diese Anwendung umfasst Folgendes:

-   Ein <xref:System.Windows.Forms.DataGridView> Steuerelement, das den Inhalt der XML-Datei als Daten anzeigt.

-   Ein <xref:System.Windows.Forms.TextBox> Steuerelement, das das XML-Schema für die XML-Datei zeigt.

-   Zwei <xref:System.Windows.Forms.Button> Steuerelemente.

    -   Eine Schaltfläche liest die XML-Datei in das Dataset und zeigt ihn in die <xref:System.Windows.Forms.DataGridView> Steuerelement.

    -   Eine zweite Schaltfläche extrahiert das Schema aus dem Dataset, und über eine <xref:System.IO.StringWriter> zeigt es in der <xref:System.Windows.Forms.TextBox> Steuerelement.

#### <a name="to-add-controls-to-the-form"></a>So fügen Sie dem Formular Steuerelemente hinzu

1.  Open `Form1` in der Entwurfsansicht.

2.  Aus der **Toolbox**, ziehen Sie die folgenden Steuerelemente auf dem Formular:

    -   Ein <xref:System.Windows.Forms.DataGridView> Steuerelement

    -   Ein <xref:System.Windows.Forms.TextBox> Steuerelement

    -   Zwei <xref:System.Windows.Forms.Button> Steuerelemente

3.  Legen Sie die folgenden Eigenschaften fest:

    |Steuerelement|Eigenschaft|Einstellung|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Bildlaufleisten**|**Vertikal**|
    |`Button1`|**Name**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Name**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Erstellen Sie das Dataset, das die XML-Daten empfängt.
 In diesem Schritt erstellen Sie ein neues Dataset mit dem Namen `authors`. Weitere Informationen über Datasets finden Sie unter [Dataset-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that-receives-the-xml-data"></a>Um ein neues Dataset zu erstellen, die die XML-Daten empfängt

1.  In **Projektmappen-Explorer**, wählen Sie die Quelldatei für **Form1**, und wählen Sie dann die **Sicht-Designer** Schaltfläche auf der **Projektmappen-Explorer** Symbolleiste.

2.  Aus der [Toolbox, Registerkarte "Daten"](../ide/reference/toolbox-data-tab.md), ziehen Sie eine **DataSet** auf **Form1**.

3.  In der **Dataset hinzufügen** wählen Sie im Dialogfeld **nicht typisiertes Dataset**, und wählen Sie dann **OK**.

     **DataSet1** wird der Komponentenleiste hinzugefügt.

4.  In der **Eigenschaften** legen die **Namen** und <xref:System.Data.DataSet.DataSetName%2A> Eigenschaften für`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Erstellen Sie den Ereignishandler zum Lesen der XML-Datei in das dataset
 Die **XML lesen** Schaltfläche liest die XML-Datei in das Dataset. Klicken Sie dann legt Eigenschaften fest, auf die <xref:System.Windows.Forms.DataGridView> Steuerelement, das an das Dataset binden.

#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>So ReadXmlButton_Click-Ereignishandler Code hinzu

1.  In **Projektmappen-Explorer**Option **Form1**, und wählen Sie dann die **Sicht-Designer** Schaltfläche auf der **Projektmappen-Explorer** Symbolleiste.

2.  Wählen Sie die **XML lesen** Schaltfläche.

     Die **Code-Editor** wird geöffnet, auf die `ReadXmlButton_Click` -Ereignishandler.

3.  Geben Sie den folgenden Code in die `ReadXmlButton_Click` Ereignishandler:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  In der `ReadXMLButton_Click` Ereignishandlercode, Änderung der `filepath =` Eintritt in den richtigen Pfad.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Erstellen Sie die Ereignishandler, um das Schema im Textfeld anzuzeigen.
 Die **Schema anzeigen** Schaltfläche erstellt eine <xref:System.IO.StringWriter> Objekt, das mit dem Schema gefüllt wird, und wird angezeigt, der <xref:System.Windows.Forms.TextBox>Steuerelement.

#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Der ShowSchemaButton_Click-Ereignishandler Code hinzu

1.  In **Projektmappen-Explorer**Option **Form1**, und wählen Sie dann die **Sicht-Designer** Schaltfläche.

2.  Wählen Sie die **Schema anzeigen** Schaltfläche.

     Die **Code-Editor** wird geöffnet, auf die `ShowSchemaButton_Click` -Ereignishandler.

3.  Geben Sie den folgenden Code in der `ShowSchemaButton_Click` -Ereignishandler.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Testen Sie das Formular
 Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten wie erwartet ausfällt.

#### <a name="to-test-the-form"></a>So testen Sie das Formular

1.  Wählen Sie **F5** um die Anwendung auszuführen.

2.  Wählen Sie die **XML lesen** Schaltfläche.

     DataGridView zeigt den Inhalt der XML-Datei.

3.  Wählen Sie die **Schema anzeigen** Schaltfläche.

     Das Textfeld zeigt die XML-Schema für die XML-Datei.

## <a name="next-steps"></a>Nächste Schritte
 In dieser exemplarischen Vorgehensweise erfahren Sie die Grundlagen der Einlesen einer XML-Datei in ein Dataset sowie das Erstellen eines Schemas, die basierend auf dem Inhalt der XML-Datei. Hier sind einige Aufgaben, die Sie als Nächstes tun können:

-   Bearbeiten Sie die Daten im Dataset und Zurückschreiben als XML. Weitere Informationen finden Sie unter <xref:System.Data.DataSet.WriteXml%2A>.

-   Bearbeiten Sie die Daten im Dataset, und schreibt sie in einer Datenbank. Weitere Informationen finden Sie unter [speichern Daten](../data-tools/saving-data.md).

## <a name="see-also"></a>Siehe auch

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [XML-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)