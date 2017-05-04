---
title: "Gewusst wie: Programmgesteuertes Sch&#252;tzen von Arbeitsbl&#228;ttern | Microsoft Docs"
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
  - "Dokumentschutz, Hinzufügen zu Arbeitsblättern"
  - "Dokumente [Office-Entwicklung in Visual Studio], Dokumentschutz"
  - "Schutz, Hinzufügen zu Arbeitsblättern"
  - "Arbeitsblätter, Schutz"
ms.assetid: 50bde1ff-918a-42ca-ba1b-f22139f8717a
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Gewusst wie: Programmgesteuertes Sch&#252;tzen von Arbeitsbl&#228;ttern
  Die Schutzfunktion in Microsoft Office Excel verhindert, dass Objekte in einem Arbeitsblatt durch Benutzer und Code geändert werden.  Standardmäßig werden alle Zellen gesperrt, nachdem der Schutz aktiviert wurde.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 In Anpassungen auf Dokumentebene können Sie Arbeitsblätter mit dem Excel\-Designer schützen.  Sie können ein Arbeitsblatt in einem beliebigen Projekttyp auch zur Laufzeit programmgesteuert schützen.  
  
> [!NOTE]  
>  Geschützten Bereichen eines Arbeitsblatts können keine Windows Forms\-Steuerelemente hinzugefügt werden.  
  
## Mithilfe des Designers  
  
#### So schützen Sie ein Arbeitsblatt im Designer  
  
1.  Klicken Sie auf der Registerkarte **Überprüfen** in der Gruppe **Änderungen** auf **Blatt schützen**.  
  
     Das Dialogfeld **Blatt schützen** wird angezeigt.  Sie können ein Kennwort festlegen und optional bestimmte Aktionen angeben, die Benutzer in einem Arbeitsblatt ausführen dürfen, z. B. Zellen formatieren oder Zeilen einfügen.  
  
 Sie können Benutzern auch die Bearbeitung bestimmter Bereiche in geschützten Arbeitsblättern erlauben.  
  
#### So lassen Sie die Bearbeitung bestimmter Bereiche zu  
  
1.  Klicken Sie auf der Registerkarte **Überprüfen** in der Gruppe **Änderungen** auf **Benutzerberechtigungen zum Bearbeiten von Bereichen**.  
  
     Das Dialogfeld **Benutzerberechtigungen zum Bearbeiten von Bereichen** wird angezeigt.  Sie können Bereiche angeben, die mithilfe eines Kennworts entsperrt werden, und Benutzer, die Bereiche ohne Kennwort bearbeiten können.  
  
## Mithilfe von Code zur Laufzeit  
 Mit dem folgenden Code wird das Kennwort \(unter Verwendung der getPasswordFromUser\-Variablen, die ein vom Benutzer angegebenes Kennwort enthält\) festgelegt und nur das Sortieren zugelassen.  
  
#### So schützen Sie ein Arbeitsblatt mithilfe von Code in einer Anpassung auf Dokumentebene  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>\-Methode des Arbeitsblatts auf.  In diesem Beispiel wird davon ausgegangen, dass Sie mit einem Arbeitsblatt namens `Sheet1` arbeiten.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#27)]  
  
#### So schützen Sie ein Arbeitsblatt mithilfe von Code in einen VSTO\-Add\-In  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A>\-Methode des aktiven Arbeitsblatts auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#17)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Aufheben des Schutzes von Arbeitsblättern](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  