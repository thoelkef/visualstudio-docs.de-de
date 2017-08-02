---
title: "Gewusst wie: Hinzuf&#252;gen von Windows&#160;Forms-Steuerelementen zu Office-Dokumenten"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Dokumente [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Windows Forms-Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen"
ms.assetid: 4d188ad2-8e17-4eb0-8422-2ff56c683e3d
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Gewusst wie: Hinzuf&#252;gen von Windows&#160;Forms-Steuerelementen zu Office-Dokumenten
  Sie können Microsoft Office Excel\- und Microsoft Office Word\-Dokumenten Windows Forms\-Steuerelemente in Projekten auf Dokumentebene zur Entwurfszeit hinzufügen.  Zur Laufzeit können Sie Steuerelemente in Anpassungen auf Dokumentebene und in VSTO\-Add\-Ins hinzufügen.  Sie können Ihrem Arbeitsblatt z. B. ein <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox>\-Steuerelement hinzufügen, um den Benutzern die Auswahl aus einer Liste von Optionen zu ermöglichen.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Hinzufügen von Steuerelementen zur Entwurfszeit](#designtime)  
  
-   [Hinzufügen von Steuerelementen in einem Projekt auf Dokumentebene zur Laufzeit](#runtimedoclevel)  
  
-   [Hinzufügen von Steuerelementen zur Laufzeit in VSTO\-Add\-Ins](#runtimeaddin)  
  
 ![Link zu Video](~/docs/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Gewusst wie: Hinzufügen von Steuerelementen zu einer Dokumentoberfläche zur Laufzeit](http://go.microsoft.com/fwlink/?LinkID=132782).  
  
##  <a name="designtime"></a> Hinzufügen von Steuerelementen zur Entwurfszeit  
 Es gibt mehrere Möglichkeiten, dem Dokument Windows Forms\-Steuerelemente in einem Projekt auf Dokumentebene zur Entwurfszeit hinzuzufügen.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### So ziehen ein Windows Forms\-Steuerelement auf das Dokument  
  
1.  Erstellen oder öffnen Sie ein Excel\-Arbeitsmappen\- oder Word\-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Klicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten, und ziehen Sie es auf das Dokument.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, wird **\=EMBED\("WinForms.Control.Host",""\)** in der **Formelleiste** angezeigt.  Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
#### So ziehen ein Windows Forms\-Steuerelement auf das Dokument  
  
1.  Erstellen oder öffnen Sie ein Excel\-Arbeitsmappen\- oder Word\-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Klicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten.  
  
3.  Klicken Sie im Dokument auf die Stelle, an der die linke obere Ecke des Steuerelements positioniert werden soll, und ziehen Sie den Mauszeiger an die Stelle, an der sich die untere rechte Ecke des Steuerelements befinden soll.  
  
     Das Steuerelement wird dem Dokument mit der angegebenen Größe und Position hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, wird **\=EMBED\("WinForms.Control.Host",""\)** in der **Formelleiste** angezeigt.  Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
#### So fügen Sie dem Dokument ein Windows Forms\-Steuerelement durch einfaches Klicken auf das Steuerelement hinzu  
  
1.  Erstellen oder öffnen Sie ein Excel\-Arbeitsmappen\- oder Word\-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Klicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten.  
  
3.  Klicken Sie im Dokument auf die Stelle, an der das Steuerelement hinzugefügt werden soll.  
  
     Das Steuerelement wird dem Dokument mit der Standardgröße hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, wird **\=EMBED\("WinForms.Control.Host",""\)** in der **Formelleiste** angezeigt.  Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
#### So fügen Sie dem Dokument ein Windows Forms\-Steuerelement durch Doppelklicken auf das Steuerelement hinzu  
  
1.  Erstellen oder öffnen Sie ein Excel\-Arbeitsmappen\- oder Word\-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Doppelklicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten.  
  
     Das Steuerelement wird dem Dokument in der Mitte des Dokuments oder des aktiven Bereichs hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, wird **\=EMBED\("WinForms.Control.Host",""\)** in der **Formelleiste** angezeigt.  Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
#### So fügen Sie dem Dokument ein Windows Forms\-Steuerelement durch Drücken der EINGABETASTE hinzu  
  
1.  Erstellen oder öffnen Sie ein Excel\-Arbeitsmappen\- oder Word\-Dokumentprojekt in Visual Studio, damit das Dokument im Designer angezeigt wird.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Klicken Sie auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** auf das Steuerelement, das Sie hinzufügen möchten, und drücken Sie die EINGABETASTE.  
  
     Das Steuerelement wird dem Dokument in der Mitte des Dokuments oder des aktiven Bereichs hinzugefügt.  
  
    > [!NOTE]  
    >  Wenn Sie in Excel ein Steuerelement auswählen, wird **\=EMBED\("WinForms.Control.Host",""\)** in der **Formelleiste** angezeigt.  Dieser Text ist erforderlich und sollte nicht gelöscht werden.  
  
##  <a name="runtimedoclevel"></a> Hinzufügen von Steuerelementen in einem Projekt auf Dokumentebene zur Laufzeit  
 Sie können einem Dokument Windows Forms\-Steuerelemente zur Laufzeit programmgesteuert hinzufügen.  Verwenden Sie in Word die Methoden der <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A>\-Eigenschaft der `ThisDocument`\-Klasse.  Verwenden Sie in Excel die Methoden der <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A>\-Eigenschaft einer `Sheet`*n*\-Klasse.  Jede Methode verfügt über mehrere Überladungen, mit denen Sie die Position des Steuerelements auf unterschiedliche Weisen angeben können.  
  
 Wenn Sie einem Dokument ein Windows Forms\-Steuerelement zur Laufzeit hinzufügen, wird das Steuerelement nicht im Dokument beibehalten, wenn das Dokument geschlossen wird.  Sie können das Steuerelement beim nächsten Öffnen des Dokuments erneut erstellen.  Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### So fügen Sie ein Windows Forms\-Steuerelement zur Laufzeit hinzu  
  
1.  Verwenden Sie eine Methode namens Add\<*Steuerelementklasse*\> \(wobei *Steuerelementklasse* der Klassenname des hinzuzufügenden Windows Forms\-Steuerelements ist, z. B. <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
     Das folgende Codebeispiel veranschaulicht das Hinzufügen von <xref:Microsoft.Office.Tools.Excel.Controls.Button> zur Zelle **C5** von `Sheet1` in einem Projekt auf Dokumentebene für Excel.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#4)]  
  
##  <a name="runtimeaddin"></a> Hinzufügen von Steuerelementen zur Laufzeit in VSTO\-Add\-Ins  
 Sie können einem beliebigen geöffneten Dokument zur Laufzeit Windows Forms\-Steuerelemente hinzufügen.  Generieren Sie zuerst ein Hostelement, das auf einem geöffneten Dokument oder Arbeitsblatt basiert.  Verwenden Sie in Word die Methoden der <xref:Microsoft.Office.Tools.Word.Document.Controls%2A>\-Eigenschaft des neuen Hostelements.  Verwenden Sie in Excel die Methoden der <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A>\-Eigenschaft des neuen Hostelements.  Jede Methode verfügt über mehrere Überladungen, mit denen Sie die Position des Steuerelements auf unterschiedliche Weisen angeben können.  
  
 Wenn Sie einem Dokument ein Windows Forms\-Steuerelement zur Laufzeit hinzufügen, wird das Steuerelement nicht im Dokument beibehalten, wenn das Dokument geschlossen wird.  Sie können das Steuerelement beim nächsten Öffnen des Dokuments erneut erstellen.  Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Weitere Informationen zum Generieren von Hostelementen in VSTO\-Add\-In\-Projekten finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### So fügen Sie ein Windows Forms\-Steuerelement zur Laufzeit hinzu  
  
1.  Verwenden Sie eine Methode namens Add\<*Steuerelementklasse*\> \(wobei *Steuerelementklasse* der Klassenname des hinzuzufügenden Windows Forms\-Steuerelements ist, z. B. <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
    > [!NOTE]  
    >  In VSTO\-Add\-In\-Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, müssen Sie einen Verweis auf die Assembly Microsoft.Office.Tools.Excel.v4.0.Utilities.dll oder Microsoft.Office.Tools.Word.v4.0.Utilities.dll hinzufügen, bevor Sie auf die Add\<*Steuerelementklasse*\>\-Methoden zugreifen können.  
  
     Das folgende Codebeispiel veranschaulicht das Hinzufügen von <xref:Microsoft.Office.Tools.Word.Controls.Button> im ersten Absatz des aktiven Dokuments mithilfe eines Word\-VSTO\-Add\-Ins.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDynamicControls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#7)]  
  
## Siehe auch  
 [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Gewusst wie: Ändern der Größe von Steuerelementen innerhalb der Arbeitsblattzellen](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  