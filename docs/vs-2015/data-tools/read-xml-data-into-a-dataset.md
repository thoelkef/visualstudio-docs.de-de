---
title: Liest XML-Daten in ein Dataset | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 18f3c5c1e3b3c19f3cbf490aa3dd71c854abe7df
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946630"
---
# <a name="read-xml-data-into-a-dataset"></a>Laden von Daten in ein Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
ADO.NET stellt einfache Methoden zum Arbeiten mit XML-Daten bereit. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows-Anwendung, die XML-Daten in ein Dataset lädt. Das Dataset wird dann angezeigt, einem <xref:System.Windows.Forms.DataGridView> Steuerelement. Abschließend wird ein XML-Schema basierend auf dem Inhalt der XML-Datei in einem Textfeld angezeigt.  
  
 In dieser exemplarischen Vorgehensweise besteht aus fünf wichtigen Schritte durchführen:  
  
1.  Erstellen eines neuen Projekts  
  
2.  Erstellen eine XML-Datei in das Dataset gelesen werden  
  
3.  Erstellen der Benutzeroberfläche  
  
4.  Erstellen des Datasets, lesen die XML-Datei und Anzeige in einem <xref:System.Windows.Forms.DataGridView> Steuerelement  
  
5.  Hinzufügen von Code zum Anzeigen des XML-Schemas auf Grundlage der XML-Datei in eine <xref:System.Windows.Forms.TextBox> Steuerelement  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle, die Sie sehen, die je nach Ihren aktiven Einstellungen oder die Edition in der Hilfe beschriebenen unterscheiden kann, das Sie verwenden. So ändern Sie Ihre Einstellungen, auf die **Tools** , wählen Sie im Menü**Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Erstellt ein neues Projekt  
 In diesem Schritt erstellen Sie ein Visual Basic oder Visual C#-Projekt, das in dieser exemplarischen Vorgehensweise enthält.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1.  Auf der **Datei** Menü ein neues Projekt erstellen.  
  
2.  Benennen Sie das Projekt mit `ReadingXML`.  
  
3.  Wählen Sie **Windows-Anwendung**, und wählen Sie dann **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Die **ReadingXML** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generieren der XML-Datei in das Dataset gelesen werden  
 Da in dieser exemplarischen Vorgehensweise konzentriert sich auf das Lesen von XML-Daten in ein Dataset, wird der Inhalt einer XML-Datei bereitgestellt.  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Die XML-Datei zu erstellen, die in das Dataset gelesen werden  
  
1.  Auf der **Projekt** , wählen Sie im Menü**neues Element hinzufügen**.  
  
2.  Wählen Sie **XML-Datei**, nennen Sie die Datei `authors.xml`, und wählen Sie dann **hinzufügen**.  
  
     Die XML-Datei in den Designer geladen, und ist für die Bearbeitung bereit.  
  
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
  
4.  Auf der **Datei** , wählen Sie im Menü**authors.xml speichern**.  
  
## <a name="create-the-user-interface"></a>Erstellen der Benutzeroberfläche  
 Die Benutzeroberfläche für diese Anwendung besteht aus den folgenden:  
  
-   Ein <xref:System.Windows.Forms.DataGridView> Steuerelement, das den Inhalt der XML-Datei als Daten anzeigt.  
  
-   Ein <xref:System.Windows.Forms.TextBox> Steuerelement, das das XML-Schema für die XML-Datei anzeigt.  
  
-   Zwei <xref:System.Windows.Forms.Button> Steuerelemente.  
  
    -   Eine Schaltfläche liest die XML-Datei in das Dataset, und zeigt ihn in das <xref:System.Windows.Forms.DataGridView> Steuerelement.  
  
    -   Eine zweite Schaltfläche extrahiert das Schema aus dem Dataset, und über eine <xref:System.IO.StringWriter> zeigt sie in der <xref:System.Windows.Forms.TextBox> Steuerelement.  
  
#### <a name="to-add-controls-to-the-form"></a>So fügen Sie dem Formular Steuerelemente hinzu  
  
1.  Open `Form1` in der Entwurfsansicht.  
  
2.  Von der **Toolbox**, ziehen Sie die folgenden Steuerelemente im Formular:  
  
    -   Eine <xref:System.Windows.Forms.DataGridView> Steuerelement  
  
    -   Eine <xref:System.Windows.Forms.TextBox> Steuerelement  
  
    -   Zwei <xref:System.Windows.Forms.Button> Steuerelemente  
  
3.  Legen Sie die folgenden Eigenschaften fest:  
  
    |Steuerelement|Eigenschaft|Einstellung|  
    |-------------|--------------|-------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**Vertikal**|  
    |`Button1`|**Name**|`ReadXmlButton`|  
    ||**Text**|`Read XML`|  
    |`Button2`|**Name**|`ShowSchemaButton`|  
    ||**Text**|`Show Schema`|  
  
## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Erstellen Sie das Dataset Thatreceives die XML-Daten  
 In diesem Schritt erstellen Sie ein neues Dataset mit dem Namen `authors`. Weitere Informationen über Datasets finden Sie unter [datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Um ein neues Dataset zu erstellen, das die XML-Daten empfängt  
  
1.  In **Projektmappen-Explorer**, wählen Sie die Quelldatei für **Form1**, und wählen Sie dann die **Ansicht-Designer** Schaltfläche der **Projektmappen-Explorer** die Symbolleiste.  
  
2.  Von der [in der Toolbox, Registerkarte "Daten"](../ide/reference/toolbox-data-tab.md), ziehen Sie eine **DataSet** auf **Form1**.  
  
3.  In der **Dataset hinzufügen** wählen Sie im Dialogfeld **nicht typisiertes Dataset**, und wählen Sie dann **OK**.  
  
     **"DataSet1"** wird der Komponentenleiste hinzugefügt.  
  
4.  In der **Eigenschaften** legen die **Namen** und <xref:System.Data.DataSet.DataSetName%2A> Eigenschaften für`AuthorsDataSet`.  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Erstellen Sie den Ereignishandler zum Lesen von XML-Datei in das dataset  
 Die **XML lesen** Schaltfläche liest die XML-Datei in das Dataset. Klicken Sie dann legt Eigenschaften fest, auf die <xref:System.Windows.Forms.DataGridView> -Steuerelement, das sie an das Dataset zu binden.  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>So ReadXmlButton_Click-Ereignishandler Code hinzu  
  
1.  In **Projektmappen-Explorer**Option **Form1**, und wählen Sie dann die **Ansicht-Designer** Schaltfläche der **Projektmappen-Explorer** Symbolleiste.  
  
2.  Wählen Sie die **XML lesen** Schaltfläche.  
  
     Die **Code-Editor** wird geöffnet, auf die `ReadXmlButton_Click` -Ereignishandler.  
  
3.  Geben Sie den folgenden Code in die `ReadXmlButton_Click` -Ereignishandler:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]  
  
4.  In der `ReadXMLButton_Click` Ereignishandlercode, Änderung der `filepath =` Eintrag auf den richtigen Pfad.  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Erstellen Sie den Ereignishandler, um das Schema in das Textfeld anzuzeigen.  
 Die **Schema anzeigen** Schaltfläche erstellt eine <xref:System.IO.StringWriter> -Objekt, mit dem Schema gefüllt ist, und wird angezeigt, in, der <xref:System.Windows.Forms.TextBox>Steuerelement.  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Die ShowSchemaButton_Click-Ereignishandler Code hinzufügen  
  
1.  In **Projektmappen-Explorer**Option **Form1**, und wählen Sie dann die **Ansicht-Designer** Schaltfläche.  
  
2.  Wählen Sie die **Schema anzeigen** Schaltfläche.  
  
     Die **Code-Editor** wird geöffnet, auf die `ShowSchemaButton_Click` -Ereignishandler.  
  
3.  Geben Sie den folgenden Code in die `ShowSchemaButton_Click` -Ereignishandler.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Testen Sie das Formular  

Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten wie erwartet ausfällt.
  
1.  Wählen Sie **F5** zum Ausführen der Anwendung.  
  
2.  Wählen Sie die **XML lesen** Schaltfläche.  
  
     DataGridView zeigt den Inhalt der XML-Datei.  
  
3.  Wählen Sie die **Schema anzeigen** Schaltfläche.  
  
     Das Textfeld zeigt die XML-Schema für die XML-Datei.  
  
## <a name="next-steps"></a>Nächste Schritte  

In dieser exemplarischen Vorgehensweise erfahren Sie, die Grundlagen der Einlesen einer XML-Datei in ein Dataset sowie das Erstellen eines Schemas, die basierend auf dem Inhalt der XML-Datei. Hier sind einige Aufgaben, die Sie als Nächstes tun können:  
  
-   Bearbeiten Sie die Daten in das Dataset und das zurückschreiben können als XML. Weitere Informationen finden Sie unter <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Bearbeiten Sie die Daten im Dataset und schreibt sie in einer Datenbank.
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [XML-Tools in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)