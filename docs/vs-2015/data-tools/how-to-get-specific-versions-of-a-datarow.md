---
title: 'Vorgehensweise: Abrufen spezifischer Versionen einer DataRow | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: ed409bdafaa15052a7190480a7cbc46ac766de84
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511015"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>Gewusst wie: Abrufen spezifischer Versionen einer DataRow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn an Datenzeilen Änderungen vorgenommen werden, werden im Dataset sowohl die ursprüngliche (<xref:System.Data.DataRowVersion>) als auch die neue (<xref:System.Data.DataRowVersion>) Version der Zeile beibehalten. Vor dem Aufruf der `AcceptChanges`-Methode kann die Anwendung z. B. auf die verschiedenen (in der <xref:System.Data.DataRowVersion>-Enumeration definierten) Versionen eines Datensatzes zugreifen und die Änderungen entsprechend verarbeiten.  
  
> [!NOTE]
>  Verschiedene Versionen einer Zeile sind nur verfügbar, wenn diese schon bearbeitet, die `AcceptChanges`-Methode jedoch noch nicht aufgerufen wurde. Nach dem Aufruf der `AcceptChanges`-Methode sind die ursprüngliche und die aktuelle Version identisch.  
  
 Wenn Sie den <xref:System.Data.DataRowVersion>-Wert zusammen mit dem Spaltenindex (oder dem Spaltennamen als Zeichenfolge) übergeben, wird der Wert der spezifischen Zeilenversion aus dieser Spalte zurückgegeben. Die geänderte Spalte wird während der Ausführung des <xref:System.Data.DataTable.ColumnChanging>-Ereignisses und des <xref:System.Data.DataTable.ColumnChanged>-Ereignisses identifiziert. Dies ist darum der geeignete Zeitpunkt, um die unterschiedlichen Zeilenversionen zu Validierungszwecken zu untersuchen. Wenn Sie Einschränkungen jedoch vorübergehend deaktiviert haben, werden diese Ereignisse nicht ausgelöst, sodass die geänderten Spalten programmgesteuert ermittelt werden müssen. Sie können dazu die <xref:System.Data.DataTable.Columns%2A>-Auflistung durchlaufen und die unterschiedlichen <xref:System.Data.DataRowVersion>-Werte vergleichen.  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>Zugreifen auf die ursprüngliche Version einer DataRow  
  
#### <a name="to-get-the-original-version-of-a-record"></a>So rufen Sie die ursprüngliche Datensatzversion ab  
  
-   Greifen Sie auf den Wert einer Spalte zu, und übergeben Sie die <xref:System.Data.DataRowVersion> der Zeile, die zurückgegeben werden soll.  
  
     Das folgende Beispiel veranschaulicht, wie Sie mithilfe eines <xref:System.Data.DataRowVersion>-Werts den ursprünglichen Wert eines `CompanyName`-Felds in einer <xref:System.Data.DataRow> abrufen:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>Zugreifen auf die aktuelle Version einer DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>So rufen Sie die aktuelle Datensatzversion ab  
  
-   Greifen Sie auf einen Spaltenwert zu, und fügen Sie dem Index einen Parameter hinzu, durch den die zurückzugebende Zeilenversion angegeben wird.  
  
     Im folgenden Beispiel wird veranschaulicht, wie Sie mithilfe eines <xref:System.Data.DataRowVersion>-Werts den aktuellen Wert eines `CompanyName`-Felds in einer <xref:System.Data.DataRow> abrufen:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)