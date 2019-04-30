---
title: 'Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem server'
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 510d923d2503aeb6e07859813537c9094fe25b09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419704"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem server
  Sie können ein Datenelement im Dokument zwischengespeichert werden markieren, damit sie verfügbar ist offline. Dies erleichtert auch möglich, dass die Daten in das Dokument durch anderen Code bearbeitet werden, wenn das Dokument auf einem Server gespeichert ist.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Sie können ein Datenelement zwischengespeichert werden, wenn das Datenelement in Ihrem Code deklariert ist, oder, bei Verwendung von markieren eine <xref:System.Data.DataSet>, durch Festlegen einer Eigenschaft in der **Eigenschaften** Fenster. Wenn Sie ein Datenelement zwischenspeichern, die keinem <xref:System.Data.DataSet> oder <xref:System.Data.DataTable>, stellen Sie sicher, dass es sich um die Kriterien für die Zwischenspeicherung im Dokument erfüllt. Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).

> [!NOTE]
> Datasets, die mit Visual Basic, der als gekennzeichnet sind erstellt **Cached** und **WithEvents** (einschließlich Datasets, die von gezogen werden die **Datenquellen** Fenster oder **Toolbox** verfügen, die die **CacheInDocument** -Eigenschaftensatz auf **"true"**) haben Sie einen Unterstrich als Präfix versehen im Cache. Wenn Sie ein Dataset erstellen, und nennen Sie sie z. B. **Kunden**, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> wird als Name **_Customers** im Cache. Bei Verwendung von <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> um diese zwischengespeicherten Element zuzugreifen, müssen Sie angeben **_Customers** anstelle von **Kunden**.

### <a name="to-cache-data-in-the-document-using-code"></a>Zum Zwischenspeichern von Daten in das Dokument mithilfe von code

1. Deklarieren Sie ein öffentliches Feld oder eine Eigenschaft für das Datenelement als Member einer Hostelementklasse in Ihrem Projekt, z. B. die `ThisDocumen`t-Klasse in einem Word-Projekt oder die `ThisWorkbook` Klasse in einem Excel-Projekt.

2. Anwenden der <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> -Attribut auf das Element, markieren Sie das Datenelement in Datencache des Dokuments gespeichert werden. Im folgenden Beispiel wird dieses Attribut einer Felddeklaration für einen <xref:System.Data.DataSet>.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. Fügen Sie Code zum Erstellen einer Instanz des Datenelements und, sofern zutreffend, um es aus der Datenbank zu laden.

     Das Datenelement wird nur geladen, wenn er erstmals erstellt wird; danach der Cache bleibt mit dem Dokument ein, und müssen Sie anderen Code, um sie zu aktualisieren schreiben.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Um ein Dataset im Dokument zwischenspeichern, indem Sie mithilfe des Eigenschaftenfensters

1. Fügen Sie das Dataset auf das Projekt mithilfe von Tools in Visual Studio-Designer, z. B. durch Hinzufügen einer Datenquelle, dem Projekt mit der **Datenquellen** Fenster.

2. Erstellen Sie eine Instanz des Datasets, wenn Sie nicht bereits einen haben, und wählen Sie die Instanz im Designer.

3. In der **Eigenschaften** legen die **CacheInDocument** Eigenschaft **"true"**.

     Weitere Informationen finden Sie unter [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md).

4. In der **Eigenschaften** legen die **Modifizierer** Eigenschaft **öffentliche** (der Standardwert ist **intern**).

## <a name="see-also"></a>Siehe auch
- [Zwischenspeichern von Daten](../vsto/caching-data.md)
- [Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Zugreifen auf Daten in Dokumenten auf dem server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Speichern von Daten](../data-tools/saving-data.md)
