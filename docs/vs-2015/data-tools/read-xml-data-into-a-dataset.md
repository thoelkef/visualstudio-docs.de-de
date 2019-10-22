---
title: Lesen von XML-Daten in ein DataSet | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c34fb87c02ff60d9b28c43130d6fbf3a12e70349
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652893"
---
# <a name="read-xml-data-into-a-dataset"></a>Laden von Daten in ein Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET stellt einfache Methoden zum Arbeiten mit XML-Daten bereit. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows-Anwendung, die XML-Daten in ein Dataset lädt. Das DataSet wird dann in einem <xref:System.Windows.Forms.DataGridView>-Steuerelement angezeigt. Schließlich wird ein XML-Schema, das auf dem Inhalt der XML-Datei basiert, in einem Textfeld angezeigt.

 Diese exemplarische Vorgehensweise besteht aus fünf Hauptschritten:

1. Erstellen eines neuen Projekts

2. Erstellen einer XML-Datei, die in das DataSet eingelesen werden soll

3. Erstellen der Benutzeroberfläche

4. Erstellen des Datasets, Lesen der XML-Datei und Anzeigen des Datasets in einem <xref:System.Windows.Forms.DataGridView>-Steuerelement

5. Hinzufügen von Code zum Anzeigen des XML-Schemas basierend auf der XML-Datei in einem <xref:System.Windows.Forms.TextBox>-Steuerelement

> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der von Ihnen verwendeten Edition von den in der Hilfe beschriebenen unterscheiden. Um die Einstellungen zu ändern, wählen **Sie im Menü Extras die Option** **Einstellungen importieren und exportieren**aus. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt
 In diesem Schritt erstellen Sie eine Visual Basic oder ein visuelles C# Projekt, das diese exemplarische Vorgehensweise enthält.

#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt

1. Erstellen Sie im Menü **Datei** ein neues Projekt.

2. Benennen Sie das Projekt mit `ReadingXML`.

3. Wählen Sie **Windows-Anwendung**aus, und klicken Sie dann auf **OK**. Weitere Informationen finden Sie unter [Client Anwendungen](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Das Projekt " **leseringxml** " wird erstellt und **Projektmappen-Explorer**hinzugefügt.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generieren der XML-Datei, die in das DataSet eingelesen werden soll
 Da sich diese exemplarische Vorgehensweise auf das Lesen von XML-Daten in ein DataSet konzentriert, wird der Inhalt einer XML-Datei bereitgestellt.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>So erstellen Sie die XML-Datei, die in das DataSet eingelesen wird

1. Wählen Sie im Menü **Projekt** die Option**Neues Element hinzufügen**aus.

2. Wählen Sie **XML-Datei**aus, benennen Sie die Datei `authors.xml`, und wählen Sie dann **Hinzufügen**.

     Die XML-Datei wird in den Designer geladen und ist zum Bearbeiten bereit.

3. Fügen Sie den folgenden Code in den Editor unterhalb der XML-Deklaration ein:

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

4. Wählen Sie im Menü **Datei** die Option**Authors. XML speichern**aus.

## <a name="create-the-user-interface"></a>Erstellen der Benutzeroberfläche
 Die Benutzeroberfläche für diese Anwendung besteht aus folgendem:

- Ein <xref:System.Windows.Forms.DataGridView> Steuerelement, das den Inhalt der XML-Datei als Daten anzeigt.

- Ein <xref:System.Windows.Forms.TextBox> Steuerelement, das das XML-Schema für die XML-Datei anzeigt.

- Zwei <xref:System.Windows.Forms.Button>-Steuerelemente.

  - Eine Schaltfläche liest die XML-Datei in das DataSet und zeigt Sie im <xref:System.Windows.Forms.DataGridView> Steuerelement an.

  - Eine zweite Schaltfläche extrahiert das Schema aus dem DataSet, und in einem <xref:System.IO.StringWriter> das im <xref:System.Windows.Forms.TextBox> Steuerelement angezeigt wird.

#### <a name="to-add-controls-to-the-form"></a>So fügen Sie dem Formular Steuerelemente hinzu

1. Öffnen Sie `Form1` in der Entwurfs Ansicht.

2. Ziehen Sie die folgenden Steuerelemente aus der **Toolbox**auf das Formular:

    - Ein <xref:System.Windows.Forms.DataGridView> Steuerelement

    - Ein <xref:System.Windows.Forms.TextBox> Steuerelement

    - Zwei <xref:System.Windows.Forms.Button> Steuerelemente

3. Legen Sie die folgenden Eigenschaften fest:

    |Steuerelement|property|Einstellung|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**ScrollBars**|**Vertikal**|
    |`Button1`|**Name**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Name**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Erstellen des Datasets, das die XML-Daten empfängt
 In diesem Schritt erstellen Sie ein neues Dataset mit dem Namen `authors`. Weitere Informationen zu Datasets finden Sie unter [DataSet-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>So erstellen Sie ein neues DataSet, das die XML-Daten empfängt

1. Wählen Sie in **Projektmappen-Explorer**die Quelldatei für **Form1**aus, und wählen Sie dann auf der Symbolleiste **Projektmappen-Explorer** die Schaltfläche **Designer anzeigen** aus.

2. Ziehen Sie ein **DataSet** auf der [Registerkarte "Toolbox", "Daten](../ide/reference/toolbox-data-tab.md)" auf **Form1**.

3. Wählen Sie im Dialogfeld **DataSet hinzufügen** die Option **nicht typisiertes DataSet**aus, und klicken Sie dann auf **OK**.

     **DataSet1** wird der Komponenten Leiste hinzugefügt.

4. Legen Sie im Fenster **Eigenschaften** die Eigenschaften **Name** und <xref:System.Data.DataSet.DataSetName%2A> für `AuthorsDataSet` fest.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Erstellen des Ereignis Handlers zum Lesen der XML-Datei in das DataSet
 Die Schaltfläche **XML lesen** liest die XML-Datei in das DataSet. Anschließend werden Eigenschaften für das <xref:System.Windows.Forms.DataGridView> Steuerelement festgelegt, das es an das DataSet bindet.

#### <a name="to-add-code-to-the-readxmlbutton_click-event-handler"></a>So fügen Sie dem ReadXmlButton_Click-Ereignishandler Code hinzu

1. WählenSie in Projektmappen-Explorer **Form1**aus, und wählen Sie dann auf der Symbolleiste **Projektmappen-Explorer** die Schaltfläche **Designer anzeigen** aus.

2. Wählen Sie die Schaltfläche **XML lesen** aus.

     Der **Code-Editor** wird mit dem `ReadXmlButton_Click`-Ereignishandler geöffnet.

3. Geben Sie den folgenden Code in den `ReadXmlButton_Click`-Ereignishandler ein:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]

4. Ändern Sie im `ReadXMLButton_Click`-Ereignishandlercode den `filepath =` Eintrag in den richtigen Pfad.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Erstellen Sie den Ereignishandler, um das Schema im Textfeld anzuzeigen.
 Die Schaltfläche **Schema anzeigen** erstellt ein <xref:System.IO.StringWriter> Objekt, das mit dem Schema gefüllt ist und in der <xref:System.Windows.Forms.TextBox>control angezeigt wird.

#### <a name="to-add-code-to-the-showschemabutton_click-event-handler"></a>So fügen Sie dem ShowSchemaButton_Click-Ereignishandler Code hinzu

1. Wählen Sie in **Projektmappen-Explorer**die Option **Form1**aus, und wählen Sie dann die Schaltfläche **Designer anzeigen** aus.

2. Wählen Sie die Schaltfläche **Schema anzeigen** aus.

     Der **Code-Editor** wird mit dem `ShowSchemaButton_Click`-Ereignishandler geöffnet.

3. Geben Sie den folgenden Code in den `ShowSchemaButton_Click`-Ereignishandler ein.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]

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
 Exemplarische Vorgehensweisen für [Daten](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) [zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [Vorbereiten der Anwendung auf den Empfang von Daten](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) - [XML-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
