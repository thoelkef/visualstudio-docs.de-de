---
title: "Gewusst wie: Programmgesteuertes L&#246;schen von Arbeitsbl&#228;ttern aus Arbeitsmappen"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Arbeitsmappen, Löschen von Arbeitsblättern"
  - "Arbeitsblätter, Löschen"
ms.assetid: c5ae99f0-806d-4320-a29c-75ad444fb996
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Gewusst wie: Programmgesteuertes L&#246;schen von Arbeitsbl&#228;ttern aus Arbeitsmappen
  Sie können jedes beliebige Arbeitsblatt in einer Arbeitsmappe löschen.  Verwenden Sie zum Löschen eines Arbeitsblatts das Arbeitsblatt\-Hostelement, oder greifen Sie auf das Arbeitsblatt mithilfe der Sheets\-Auflistung der Arbeitsmappe zu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Verwenden das Arbeitsblatt\-Hostelements  
 Wenn das Arbeitsblatt zur Entwurfszeit in einer Anpassung auf Dokumentebene hinzugefügt wurde, verwenden Sie die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>, um ein angegebenes Arbeitsblatt zu löschen.  Der folgende Code löscht ein Arbeitsblatt aus einer Arbeitsmappe durch direktes Verweisen auf das Arbeitsblatt\-Hostelement.  
  
> [!IMPORTANT]  
>  Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe einer der folgenden Projektvorlagen erstellen:  
>   
>  -   Excel 2013\-Arbeitsmappe  
> -   Excel 2013\-Vorlage  
> -   Excel 2010\-Arbeitsmappe  
> -   Excel 2010\-Vorlage  
>   
>  Wenn Sie diese Aufgabe mit einem anderen Projekttyp ausführen möchten, müssen Sie einen Verweis auf die **Microsoft.Office.Interop.Excel**\-Assembly hinzufügen und dann die Klassen aus dieser Assembly verwenden, um eine Arbeitsmappe zu öffnen und das Arbeitsblatt zu löschen.  Weitere Informationen finden Sie unter [Verweisen auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Referenz für primäre Interopassemblys für Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### So löschen Sie ein Arbeitsblatt mithilfe eines Arbeitsblatt\-Hostelements  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>\-Methode von `Sheet1` auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#17)]  
  
## Verwenden der Sheets\-Auflistung der Excel\-Arbeitsmappe  
 Greifen Sie auf Arbeitsblätter über die Microsoft Office Excel\-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> in den folgenden Fällen zu:  
  
-   Sie möchten ein Arbeitsblatt in einem VSTO\-Add\-In löschen.  
  
-   Das Arbeitsblatt, das Sie löschen möchten, wurde zur Laufzeit in einer Anpassung auf Dokumentebene erstellt.  
  
 Der folgende Code löscht ein Arbeitsblatt aus einer Arbeitsmappe durch Verweisen auf das Blatt über die Indexnummer der **Sheets**\-Auflistung.  Dieser Code geht davon aus, dass ein neues Arbeitsblatt programmgesteuert erstellt wurde.  
  
> [!IMPORTANT]  
>  Wenn Sie diese Aufgabe mit einem anderen Projekttyp ausführen möchten, müssen Sie einen Verweis auf die **Microsoft.Office.Interop.Excel**\-Assembly hinzufügen und dann die Klassen aus dieser Assembly verwenden, um eine Arbeitsmappe zu öffnen und das Arbeitsblatt zu löschen.  Weitere Informationen finden Sie unter [Verweisen auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Referenz für primäre Interopassemblys für Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### So löschen Sie ein Arbeitsblatt mithilfe der Sheets\-Auflistung der Excel\-Arbeitsmappe  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> der Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#18)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  