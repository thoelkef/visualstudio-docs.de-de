---
title: 'Gewusst wie: Füllen eines Datasets mit Daten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f36aa2dac656f6fd27b656d0ddfb58a758eb6487
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295996"
---
# <a name="how-to-fill-a-dataset-with-data"></a>Gewusst wie: Füllen eines Datasets mit Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Ausdruck "ein Datasets mit Daten gefüllt" bezieht sich auf die Laden von Daten in die einzelnen <xref:System.Data.DataTable> Objekte, die das Dataset bilden. Durch die TableAdapter-Abfragen oder durch Ausführen von Datenadapter, füllen Sie die Datentabellen (z. B. <xref:System.Data.SqlClient.SqlDataAdapter>) Befehle.  
  
 Gibt an, ob Sie TableAdapters oder Datenadapter verwenden sollten, hängt davon ab, wie Sie das Dataset erstellt haben. Bei Verwendung der Entwurfstools in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], z. B. die [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f), enthält das Dataset TableAdapters. Weitere Informationen zu TableAdapters finden Sie unter [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md). Wenn Sie programmgesteuert Ihr Dataset erstellt, müssen Sie in der Regel Datenadapter zum Laden von Daten in den Datentabellen zu erstellen.  
  
> [!NOTE]
>  Beim Ziehen von Elementen aus der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf ein Formular, der Code zum Füllen der Datentabelle mit Daten wird automatisch hinzugefügt der `Form_Load` -Ereignishandler. Öffnen Sie das Formular im Code-Editor, um die genaue Syntax zum Füllen der einzelnen Tabellen anzuzeigen. Wenn Sie nicht möchten, zum Auffüllen der Tabelle, wenn das Formular geladen wird, können Sie dieser Code in eine andere Methode verschieben oder entfernen Sie ihn ganz.  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>Auffüllen eines Datasets mit einem TableAdapter  
 Sie können eine Abfrage für den TableAdapter zum Laden von Daten in Datentabellen in einem Dataset aufrufen. Übergeben Sie die <xref:System.Data.DataTable> Sie für die TableAdapter-Abfrage füllen möchten. Wenn die Abfrage Parameter akzeptiert, übergeben Sie diese an die Methode auch. Wenn der Dataset mehrere Tabellen enthält, Sie müssen separate TableAdapters für jede Tabelle und müssen daher separat gefüllt werden.  
  
> [!NOTE]
>  Standardmäßig werden jedes Mal, wenn Sie beim Ausführen einer TableAdapter-Abfrage, die Daten in der Tabelle vor die Ergebnisse der Abfrage, die in die Tabelle geladen werden gelöscht. Sie können die vorhandenen Daten beibehalten, in der Tabelle und fügen Sie die Ergebnisse durch Festlegen des TableAdapter `ClearBeforeFill` Eigenschaft `false`.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>Zum Auffüllen eines Datasets mit Daten, die mit einem TableAdapter  
  
1.  Öffnen Sie das Formular oder die Komponente in der **Code-Editor**.  
  
2.  Fügen Sie Code an einer beliebigen Stelle in Ihrer Anwendung Sie eine Datentabelle mit Daten zu laden müssen. Wenn Ihre Abfrage keine Parameter akzeptiert, übergeben Sie die <xref:System.Data.DataTable> Sie füllen möchten. Der Code sollte etwa wie folgt aussehen:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  Wenn die Abfrage Parameter akzeptiert, übergeben Sie die <xref:System.Data.DataTable> Füllung und den Parametern, die von der Abfrage erwarteten werden sollen. Abhängig von den tatsächlichen Parametern in Ihrer Abfrage würde der Code in den folgenden Beispielen ähnlich aussehen:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>Auffüllen eines Datasets mit einen "DataAdapter"  
 Rufen Sie des Datenadapters `Fill` Methode. Dies bewirkt, dass des Adapters zum Ausführen der SQL-Anweisung oder gespeicherte Prozedur verwiesen wird, dessen `SelectCommand` Eigenschaft und die Ergebnisse in eine Tabelle im Dataset. Wenn der Dataset mehrere Tabellen enthält, Sie müssen separate Datenadapter für jede Tabelle und müssen daher separat gefüllt werden.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>Zum Auffüllen eines Datasets mit Daten, die über einen "DataAdapter"  
  
-   Rufen Sie die <xref:System.Data.Common.DataAdapter.Fill%2A> Methode der <xref:System.Data.Common.DataAdapter>, und übergeben Sie die <xref:System.Data.DataSet> oder <xref:System.Data.DataTable> zum Laden der Daten in. Zum Beispiel:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     Sie sollten in der Regel geben Sie den Namen des der <xref:System.Data.DataTable> zum Laden der Daten in. Wenn Sie den Namen der übergeben eine <xref:System.Data.DataSet> anstelle einer bestimmten Datentabelle, einen <xref:System.Data.DataTable> mit dem Namen `Table1` zum Dataset hinzugefügt und mit den Ergebnissen aus der Datenbank geladen wird (im Gegensatz zu Laden der Daten in einer vorhandenen <xref:System.Data.DataTable> im Dataset). Weitere Informationen finden Sie unter [Auffüllen eines Datasets mit einen "DataAdapter"](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
## <a name="see-also"></a>Siehe auch  
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)