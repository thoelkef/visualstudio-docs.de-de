---
title: "Vorgehensweise: Zwischenspeichern von Daten für die Verwendung Offline ist oder auf einem Server | Microsoft Docs"
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
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 44130744af5d09e8582e2589bcefb7aca11b5ce2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Gewusst wie: Zwischenspeichern von Daten zur Offlineverwendung oder zur Verwendung auf einem Server
  Sie können ein Datenelement im Dokument zwischenspeichern markieren, damit er verfügbar ist offline. Dadurch auch möglich, dass die Daten in das Dokument durch anderen Code bearbeitet werden, wenn das Dokument auf einem Server gespeichert wird.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie können ein Datenelement zwischengespeichert werden soll, wenn das Datenelement in Ihrem Code deklariert ist, oder bei Verwendung von kennzeichnen einer <xref:System.Data.DataSet>, durch Festlegen einer Eigenschaft in der **Eigenschaften** Fenster. Wenn Sie ein Datenelement zwischengespeichert werden, die keine <xref:System.Data.DataSet> oder <xref:System.Data.DataTable>, stellen Sie sicher, dass sie die Kriterien für die lösungsdatensammlung in das Dokument erfüllt. Weitere Informationen finden Sie unter [Caching Data](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Datasets erstellt mithilfe von Visual Basic, die als markiert sind **Cached** und **WithEvents** (einschließlich Datasets, die von gezogen werden die **Datenquellen** Fenster oder **Toolbox** , auf denen die **CacheInDocument** -Eigenschaftensatz auf **"true"**) einen Unterstrich in ihren Namen im Cache. Angenommen, Sie erstellen ein Dataset, und nennen Sie sie **Kunden**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> Name **_Customers** im Cache. Bei Verwendung von <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> um diese zwischengespeicherten Element zuzugreifen, müssen Sie angeben **_Customers** anstelle von **Kunden**.  
  
### <a name="to-cache-data-in-the-document-using-code"></a>Zum Zwischenspeichern von Daten in das Dokument mithilfe von code  
  
1.  Deklarieren Sie ein öffentliches Feld oder eine Eigenschaft für das Datenelement als Member einer Hostelementklasse in Ihrem Projekt, z. B. die `ThisDocumen`t-Klasse in einem Word-Projekt oder die `ThisWorkbook` -Klasse in einem Excel-Projekt.  
  
2.  Anwenden der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> -Attribut auf die Member, markieren Sie das Datenelement im Datencache des Dokuments gespeichert werden. Im folgenden Beispiel wird eine Felddeklaration für dieses Attribut gilt eine <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  Fügen Sie Code zum Erstellen einer Instanz des Datenelements und, sofern zutreffend, um es aus der Datenbank zu laden.  
  
     Das Datenelement wird nur geladen, wenn der Dienst erstmalig erstellt wird; Danach wird der Cache verbleibt im Dokument, und muss beim Schreiben von anderem Code, um ihn zu aktualisieren.  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Um ein Dataset im Dokument zwischenzuspeichern, über das Fenster "Eigenschaften"  
  
1.  Fügen Sie das Dataset mithilfe von Tools in Visual Studio-Designer, z. B. durch Hinzufügen einer Datenquelle, dem Projekt mit dem Projekt die **Datenquellen** Fenster.  
  
2.  Erstellen Sie eine Instanz des Datasets, wenn Sie nicht bereits vorhanden, und wählen Sie die Instanz im Designer.  
  
3.  In der **Eigenschaften** legen die **CacheInDocument** Eigenschaft **"true"**.  
  
     Weitere Informationen finden Sie unter [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md).  
  
4.  In der **Eigenschaften** legen die **Modifizierer** Eigenschaft, um **öffentlichen** (der Standardwert ist **intern**).  
  
## <a name="see-also"></a>Siehe auch  
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Speichern von Daten](/visualstudio/data-tools/saving-data)  
  
  