---
title: "Gewusst wie: F&#252;llen eines Datasets mit Daten | Microsoft Docs"
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
  - "Daten [Visual Basic], Laden in Datasets"
  - "Datasets [Visual Basic], Füllen"
  - "DataTable-Objekte, Laden"
  - "TableAdapter.Fill"
  - "TableAdapter.GetData"
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: F&#252;llen eines Datasets mit Daten
Das Füllen eines Datasets mit Daten bezieht sich darauf, dass Daten in die einzelnen <xref:System.Data.DataTable>\-Objekte geladen werden, aus denen das Dataset besteht.  Datentabellen werden gefüllt, indem TableAdapter\-Abfragen oder Befehle von Datenadaptern \(z. B. <xref:System.Data.SqlClient.SqlDataAdapter>\) ausgeführt werden.  
  
 Ob TableAdapters oder Datenadapter verwendet werden, hängt davon ab, wie Sie das Dataset erstellt haben.  Wenn Sie die Entwurfstools in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwenden, z. B. den [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png), enthält das Dataset TableAdapters.  Weitere Informationen zu TableAdapters finden Sie unter [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md).  Wenn Sie ein Dataset programmgesteuert erstellt haben, müssen Sie in der Regel Datenadapter erstellen, um Daten in die Datentabellen laden zu können.  
  
> [!NOTE]
>  Wenn Sie Elemente aus dem [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) auf ein Formular ziehen, wird dem `Form_Load`\-Ereignishandler automatisch der Code hinzugefügt, der die Datentabelle mit Daten füllt.  Öffnen Sie das Formular im Code\-Editor, um die genaue Syntax für das Füllen der einzelnen Tabellen anzuzeigen.  Wenn die Tabelle beim Laden des Formulars nicht gefüllt werden soll, können Sie diesen Code in eine andere Methode verschieben oder komplett löschen.  
  
## Füllen eines Datasets mithilfe eines TableAdapter  
 Sie können eine TableAdapter\-Abfrage aufrufen, um Daten in Datentabellen eines Datasets zu laden.  Übergeben Sie die zu füllende <xref:System.Data.DataTable> an die TableAdapter\-Abfrage.  Wenn die Abfrage Parameter annimmt, übergeben Sie diese ebenfalls an die Methode.  Wenn das Dataset mehrere Tabellen enthält, sollten Sie separate TableAdapter für die einzelnen Tabellen besitzen, die separat gefüllt werden müssen.  
  
> [!NOTE]
>  Immer, wenn Sie eine TableAdapter\-Abfrage ausführen, werden die Daten in der Tabelle standardmäßig gelöscht, bevor die Ergebnisse der Abfrage in die Tabelle geladen werden.  Um die bestehenden Tabellendaten beizubehalten und die Ergebnisse anzuhängen, legen Sie für die `ClearBeforeFill`\-Eigenschaft des TableAdapter `false` fest.  
  
#### So füllen Sie ein Dataset mithilfe eines TableAdapter mit Daten  
  
1.  Öffnen Sie das Formular oder die Komponente im **Code\-Editor**.  
  
2.  Fügen Sie in der Anwendung Code ein, wo Daten in eine Datentabelle geladen werden müssen.  Wenn in der Abfrage keine Parameter verwendet werden, übergeben Sie die <xref:System.Data.DataTable>, die gefüllt werden soll.  Der Code sollte ungefähr wie folgt aussehen:  
  
     [!code-cs[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_1.vb)]  
  
3.  Wenn die Abfrage Parameter verwendet, übergeben Sie die <xref:System.Data.DataTable>, die gefüllt werden soll, sowie die Parameter, die von der Abfrage erwartet werden.  Je nach den tatsächlich in der Abfrage verwendeten Parametern, würde der Code wie in den folgenden Beispielen aussehen:  
  
     [!code-cs[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_2.vb)]  
  
## Füllen eines Datasets mithilfe eines DataAdapter  
 Rufen Sie die `Fill`\-Methode des Datenadapters auf.  Dies führt dazu, dass der Adapter die SQL\-Anweisung oder die gespeicherte Prozedur ausführt, auf die in seiner `SelectCommand`\-Eigenschaft verwiesen wird. Die Ergebnisse werden in eine Tabelle im Dataset übertragen.  Wenn das Dataset mehrere Tabellen enthält, sollten Sie separate Datenadapter für die einzelnen Tabellen besitzen, die alle separat gefüllt werden müssen.  
  
#### So füllen Sie ein Dataset mithilfe eines DataAdapters mit Daten  
  
-   Rufen Sie die <xref:System.Data.Common.DataAdapter.Fill%2A>\-Methode von <xref:System.Data.Common.DataAdapter> auf, um <xref:System.Data.DataSet> oder <xref:System.Data.DataTable> zu übergeben, in die Daten geladen werden.  Beispiele:  
  
     [!code-cs[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_3.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_3.vb)]  
  
     Sie sollten i. d. R. den Namen von <xref:System.Data.DataTable> angeben, wenn Sie dorthin Daten laden möchten.  Wenn Sie statt einer bestimmten Datentabelle den Namen eines <xref:System.Data.DataSet> übergeben, wird dem Dataset die <xref:System.Data.DataTable> `Table1` hinzugefügt und mit den Ergebnissen aus der Datenbank geladen. \(Die Alternative wäre, Daten in eine vorhandene <xref:System.Data.DataTable> im Dataset zu laden.\)  Weitere Informationen finden Sie unter [Auffüllen eines DataSet mit einem DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
## Siehe auch  
 [Auffüllen von Datasets mit Daten](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)