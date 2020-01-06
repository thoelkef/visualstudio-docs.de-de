---
title: Laden von Daten in ein Dataset
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5f89645b9d5ec8ab0f69fad4fea5a399d8e6764d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586327"
---
# <a name="read-xml-data-into-a-dataset"></a>Laden von Daten in ein Dataset

ADO.NET stellt einfache Methoden zum Arbeiten mit XML-Daten bereit. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows-Anwendung, die XML-Daten in ein Dataset lädt. Das DataSet wird dann in einem <xref:System.Windows.Forms.DataGridView>-Steuerelement angezeigt. Schließlich wird ein XML-Schema, das auf dem Inhalt der XML-Datei basiert, in einem Textfeld angezeigt.

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts

Erstellen Sie ein neues **Windows Forms-App** - C# Projekt für oder Visual Basic. Benennen Sie das Projekt mit " **leseringxml**".

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generieren der XML-Datei, die in das DataSet eingelesen werden soll

Da sich diese exemplarische Vorgehensweise auf das Lesen von XML-Daten in ein DataSet konzentriert, wird der Inhalt einer XML-Datei bereitgestellt.

1. Wählen Sie im Menü **Projekt** die Option **Neues Element hinzufügen** aus.

2. Wählen Sie **XML-Datei**aus, benennen Sie die Datei **Authors. XML**, und wählen Sie dann **Hinzufügen**aus.

   Die XML-Datei wird in den Designer geladen und ist zum Bearbeiten bereit.

3. Fügen Sie die folgenden XML-Daten in den Editor unterhalb der XML-Deklaration ein:

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

4. Wählen Sie im Menü **Datei** die Option **Authors. XML speichern**aus.

## <a name="create-the-user-interface"></a>Erstellen der Benutzeroberfläche

Die Benutzeroberfläche für diese Anwendung besteht aus folgendem:

- Ein <xref:System.Windows.Forms.DataGridView> Steuerelement, das den Inhalt der XML-Datei als Daten anzeigt.

- Ein <xref:System.Windows.Forms.TextBox> Steuerelement, das das XML-Schema für die XML-Datei anzeigt.

- Zwei <xref:System.Windows.Forms.Button>-Steuerelemente.

  - Eine Schaltfläche liest die XML-Datei in das DataSet und zeigt Sie im <xref:System.Windows.Forms.DataGridView> Steuerelement an.

  - Eine zweite Schaltfläche extrahiert das Schema aus dem DataSet, und in einem <xref:System.IO.StringWriter> das im <xref:System.Windows.Forms.TextBox> Steuerelement angezeigt wird.

### <a name="to-add-controls-to-the-form"></a>So fügen Sie dem Formular Steuerelemente hinzu

1. Öffnen Sie `Form1` in der Entwurfs Ansicht.

2. Ziehen Sie die folgenden Steuerelemente aus der **Toolbox**auf das Formular:

    - Ein <xref:System.Windows.Forms.DataGridView> Steuerelement

    - Ein <xref:System.Windows.Forms.TextBox> Steuerelement

    - Zwei <xref:System.Windows.Forms.Button> Steuerelemente

3. Legen Sie die folgenden Eigenschaften fest:

    |Steuerelement|Die Eigenschaften-|-Einstellung|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**ScrollBars**|**Vertikal**|
    |`Button1`|**Name**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Name**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Erstellen des Datasets, das die XML-Daten empfängt

In diesem Schritt erstellen Sie ein neues Dataset mit dem Namen `authors`. Weitere Informationen zu Datasets finden Sie unter [DataSet-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. Wählen Sie in **Projektmappen-Explorer**die Quelldatei für **Form1**aus, und wählen Sie dann auf der Symbolleiste **Projektmappen-Explorer** die Schaltfläche **Designer anzeigen** aus.

2. Ziehen Sie ein **DataSet** auf der [Registerkarte "Toolbox", "Daten](../ide/reference/toolbox-data-tab.md)" auf **Form1**.

3. Wählen Sie im Dialogfeld **DataSet hinzufügen** die Option **nicht typisiertes DataSet**aus, und klicken Sie dann auf **OK**.

     **DataSet1** wird der Komponenten Leiste hinzugefügt.

4. Legen Sie im Fenster **Eigenschaften** die Eigenschaften **Name** und <xref:System.Data.DataSet.DataSetName%2A> für`AuthorsDataSet`fest.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Erstellen des Ereignis Handlers zum Lesen der XML-Datei in das DataSet

Die Schaltfläche **XML lesen** liest die XML-Datei in das DataSet. Anschließend werden Eigenschaften für das <xref:System.Windows.Forms.DataGridView> Steuerelement festgelegt, das es an das DataSet bindet.

1. WählenSie in Projektmappen-Explorer **Form1**aus, und wählen Sie dann auf der Symbolleiste **Projektmappen-Explorer** die Schaltfläche **Designer anzeigen** aus.

2. Wählen Sie die Schaltfläche **XML lesen** aus.

     Der **Code-Editor** wird mit dem `ReadXmlButton_Click`-Ereignishandler geöffnet.

3. Geben Sie den folgenden Code in den `ReadXmlButton_Click`-Ereignishandler ein:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. Ändern Sie im `ReadXMLButton_Click`-Ereignishandlercode den `filepath =` Eintrag in den richtigen Pfad.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Erstellen Sie den Ereignishandler, um das Schema im Textfeld anzuzeigen.

Die Schaltfläche **Schema anzeigen** erstellt ein <xref:System.IO.StringWriter> Objekt, das mit dem Schema gefüllt ist und im <xref:System.Windows.Forms.TextBox>Steuerelement angezeigt wird.

1. Wählen Sie in **Projektmappen-Explorer**die Option **Form1**aus, und wählen Sie dann die Schaltfläche **Designer anzeigen** aus.

2. Wählen Sie die Schaltfläche **Schema anzeigen** aus.

     Der **Code-Editor** wird mit dem `ShowSchemaButton_Click`-Ereignishandler geöffnet.

3. Fügen im `ShowSchemaButton_Click`-Ereignishandler den folgenden Code ein.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Testen des Formulars

Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten wie erwartet ausfällt.

1. Drücken Sie **F5** , um die Anwendung auszuführen.

2. Wählen Sie die Schaltfläche **XML lesen** aus.

     In der DataGridView wird der Inhalt der XML-Datei angezeigt.

3. Wählen Sie die Schaltfläche **Schema anzeigen** aus.

     Im Textfeld wird das XML-Schema für die XML-Datei angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Diese exemplarische Vorgehensweise vermittelt Ihnen die Grundlagen zum Lesen einer XML-Datei in ein DataSet sowie zum Erstellen eines Schemas auf der Grundlage des Inhalts der XML-Datei. Im folgenden sind einige Aufgaben aufgeführt, die Sie als nächstes ausführen können:

- Bearbeiten Sie die Daten im DataSet, und schreiben Sie Sie als XML zurück. Weitere Informationen finden Sie unter <xref:System.Data.DataSet.WriteXml%2A>.

- Bearbeiten Sie die Daten im DataSet, und schreiben Sie Sie in eine Datenbank.

## <a name="see-also"></a>Siehe auch

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [XML-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
