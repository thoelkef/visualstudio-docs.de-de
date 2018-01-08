---
title: "Vorgehensweise: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken | Microsoft Docs"
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
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 17ebd691120d1d5aba2623f8178d95c3fc142dee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Gewusst wie: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken
  Wenn Sie eine Microsoft Office Excel-Dokument zu, die Windows Forms-Steuerelemente enthält drucken, sind die Steuerelemente auf dem gedruckten Arbeitsblatt sichtbar. Sie können die Steuerelemente ausblenden beim Drucken eines Arbeitsblatts.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Wenn Sie Steuerelemente ausblenden, die Daten, wie z. B. angezeigt eine <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, die Daten in das Steuerelement ist nicht auf dem gedruckten Arbeitsblatt sichtbar.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Steuert, wann ein Arbeitsblatt ausblenden wird gedruckt  
  
1.  Erstellen oder öffnen Sie ein Excel-Projekt in Visual Studio, und überprüfen Sie, ob **"Sheet1"** im Designer angezeigt wird. Informationen zum Erstellen von Projekten finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.Controls.Button> die Steuerung an eine Zelle auf `Sheet1`.  
  
3.  In der **Eigenschaften** legen die <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> Eigenschaft **"false"**.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Windows Forms-Steuerelemente in Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Vorgehensweise: Ändern der Größe von Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  