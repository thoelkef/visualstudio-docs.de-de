---
title: 'Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e117243afff5cfa73cd7a27ad8ce0230d8fd512a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Gewusst wie: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument
  Sie können ein Datenobjekt für den Datencache in einem Dokument programmgesteuert hinzufügen, durch Aufrufen der `StartCaching` Methode von einem Host-Elements, z. B. eine <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, oder <xref:Microsoft.Office.Tools.Excel.Worksheet>. Entfernen Sie ein Datenobjekt aus dem Datencache durch Aufrufen der `StopCaching` Methode eines Hostelements.  
  
 Die `StartCaching` Methode und die `StopCaching` Methode sind private, aber sie werden in IntelliSense angezeigt.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Bei Verwendung der `StartCaching` -Methode zum Hinzufügen eines Datenobjekts für den Datencache das Datenobjekt muss nicht deklariert werden, mit der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut. Das Datenobjekt muss jedoch bestimmte Anforderungen für den Datencache hinzuzufügenden erfüllen. Weitere Informationen finden Sie unter [Caching Data](../vsto/caching-data.md).  
  
### <a name="to-programmatically-cache-a-data-object"></a>Ein Datenobjekt programmgesteuert zwischenspeichern  
  
1.  Das Datenobjekt auf Klassenebene nicht innerhalb einer Methode zu deklarieren. In diesem Beispiel wird davon ausgegangen, dass Sie deklarieren eine <xref:System.Data.DataSet> mit dem Namen `dataSet1` , die Sie programmgesteuert zwischenspeichern möchten.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  Instanziieren Sie das Datenobjekt, und rufen Sie anschließend die `StartCaching` -Methode des Dokuments oder Arbeitsblatts-Instanz, und übergeben Sie den Namen der Datenobjekt.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
### <a name="to-stop-caching-a-data-object"></a>So beenden Sie das Zwischenspeichern eines Datenobjekts  
  
1.  Rufen Sie die `StopCaching` -Methode des Dokuments oder Arbeitsblatts-Instanz, und übergeben Sie den Namen der Datenobjekt. In diesem Beispiel wird davon ausgegangen, dass Sie haben eine <xref:System.Data.DataSet> mit dem Namen `dataSet1` , die Sie Zwischenspeichern beenden möchten.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Rufen Sie nicht `StopCaching` aus den Ereignishandler für das `Shutdown` -Ereignis für ein Dokument oder Arbeitsblatt. Nach der Dauer der `Shutdown` Ereignis ausgelöst wird, ist zu spät, um den Datencache zu ändern. Weitere Informationen zu den `Shutdown` -Ereignis finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung Offline ist oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Speichern von Daten](/visualstudio/data-tools/saving-data)  
  
  