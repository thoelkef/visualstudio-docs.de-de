---
title: Die Datenquelle in Office-Dokument programmgesteuert zwischenspeichern
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e63b478fb16965f639a76dad0cbc3b2715bc7e2
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401402"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument
  Sie können ein Objekt, das dem Datencache in einem Dokument programmgesteuert hinzufügen, durch den Aufruf der `StartCaching` Methode von einem Host-Elements, z. B. eine <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, oder <xref:Microsoft.Office.Tools.Excel.Worksheet>. Entfernen Sie ein Datenobjekt aus dem Datencache durch Aufrufen der `StopCaching` Methode eines Hostelements.

 Die `StartCaching` Methode und die `StopCaching` Methode privat sind, aber sie werden in IntelliSense angezeigt.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Bei Verwendung der `StartCaching` Methode, um ein Objekt, das dem Datencache, der das Objekt hinzuzufügen, muss nicht deklariert werden, mit der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut. Allerdings erfüllt das Datenobjekt, das bestimmte Anforderungen, das dem Datencache hinzugefügt werden. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>Ein Datenobjekt programmgesteuert zwischenspeichern

1. Das Datenobjekt auf Klassenebene, nicht innerhalb einer Methode zu deklarieren. In diesem Beispiel wird davon ausgegangen, dass Sie deklarieren eine <xref:System.Data.DataSet> mit dem Namen `dataSet1` , die Sie programmgesteuert zwischenspeichern möchten.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Das Datenobjekt, das Instanziieren und rufen Sie dann die `StartCaching` Methode des Dokument oder Arbeitsblatt-Instanz, und übergeben den Namen des Datenobjekts.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>So beenden Sie das Zwischenspeichern eines Datenobjekts

1. Rufen Sie die `StopCaching` Methode des Dokument oder Arbeitsblatt-Instanz, und übergeben den Namen des Datenobjekts. In diesem Beispiel wird davon ausgegangen, dass Sie haben eine <xref:System.Data.DataSet> mit dem Namen `dataSet1` , die Sie beenden das Zwischenspeichern möchten.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > Rufen Sie keine `StopCaching` aus der Ereignishandler für die `Shutdown` Ereignis von einem Dokument oder Arbeitsblatt. Mit der Zeit die `Shutdown` Ereignis wird ausgelöst, ist es zu spät, den Datencache zu ändern. Weitere Informationen zu den `Shutdown` Ereignis finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Siehe auch

- [Zwischenspeichern von Daten](../vsto/caching-data.md)
- [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Zugreifen auf Daten in Dokumenten auf dem server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Speichern von Daten](../data-tools/saving-data.md)
