---
title: "Office-Projekte in der Visual Studio-Umgebung"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.WordDocument"
  - "VST.ProjectItem.ExcelWorkbook"
  - "VST.ProjectItem.ExcelTemplate"
  - "VST.ProjectItem.ExcelSheet"
  - "VST.ProjectItem.BlueprintCode"
  - "VST.ProjectItem.Word"
  - "VST.ProjectItem.Excel"
  - "VST.ProjectItem.AddinProject"
  - "Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner"
  - "VST.ProjectItem.ExtendedBluePrint"
  - "VST.ProjectItem.WordTemplate"
  - "Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner"
  - "VST.Designer.ExcelVST.Designer.Word"
  - "VST.ProjectItem.ExtendedBlueprintCode"
  - "VST.ProjectItem.BluePrint"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Dokumente [Office-Entwicklung in Visual Studio]"
  - "Ausgeblendete Dateien [Office-Entwicklung in Visual Studio]"
  - "Projektdateien [Office-Entwicklung in Visual Studio], ausgeblendete"
  - "Office-Entwicklung in Visual Studio, Dokumente in Visual Studio"
  - "Entwurfsansicht, Excel"
  - "Designer, Office-Entwicklung in Visual Studio"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio]"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Informationen über Dokumente in Visual Studio"
  - "Designer [Office-Entwicklung in Visual Studio]"
  - "Word-Designer"
  - "Word [Office-Entwicklung in Visual Studio], Word-Designer"
  - "Visual Studio, Office-Dokumente in"
  - "Arbeitsblätter [Office-Entwicklung in Visual Studio]"
  - "VST.Designer.ExcelVST.Designer.Word"
ms.assetid: 4bff36c9-4edd-4b28-89e6-0ea9f6caca02
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Office-Projekte in der Visual Studio-Umgebung
  Microsoft Office\-Projekte verfügen über eine ähnliche Entwicklungsumgebung wie andere Projekttypen in Visual Studio, z. B. Windows Forms\-Projekte. Wenn Sie ein Office\-Projekt erstellen oder öffnen, werden die Projektelemente im **Projektmappen\-Explorer** angezeigt. Bei Projekten auf Dokumentebene wird das Dokument \(d. h. das Word\-Dokument oder die Excel\-Arbeitsmappe\) in Visual Studio geöffnet, und das Dokument verhält sich wie ein visueller Designer.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Projektelemente im Projektmappen\-Explorer  
 In einem Projekt auf Dokumentebene werden im **Projektmappen\-Explorer** die folgenden Standardelemente angezeigt:  
  
-   Knoten für das Dokument, die Arbeitsmappe und Arbeitsblätter, die durch das Projekt angepasst werden. Diese Knoten dienen als Container für die Codedateien, die dem Dokument, der Arbeitsmappe und den Arbeitsblättern zugeordnet sind.  
  
-   Zugeordnete Codedateien für das Dokument, die Arbeitsmappe und die Arbeitsblätter, die durch das Projekt angepasst werden. In Word\-Projekten sind Codedateien dem Word\-Dokument oder der Vorlage zugeordnet. In Excel\-Projekten sind Codedateien der Excel\-Arbeitsmappe oder \-Vorlage sowie jedem Arbeitsblatt und Diagrammblatt in der Arbeitsmappe oder Vorlage zugeordnet.  
  
-   Ausgeblendete Projektdateien, die nicht für eine direkte Bearbeitung vorgesehen sind. Weitere Informationen finden Sie unter [Ausgeblendete Projektdateien](#hiddenfiles).  
  
 In einem VSTO\-Add\-In\-Projekt werden im **Projektmappen\-Explorer** die folgenden Standardelemente angezeigt:  
  
-   Der Anwendungsknoten Dieser Knoten verfügt über den gleichen Namen wie die Hostanwendung, z. B. **Word**, **Excel** oder **Outlook**. Der Anwendungsknoten enthält die ThisAddIn\-Codedatei. Er stellt auch die Eigenschaft **Namespace für Hostelement** bereit. Weitere Informationen zu dieser Eigenschaft finden Sie unter [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md).  
  
-   Die ThisAddIn\-Codedatei Diese Datei enthält die generierte `ThisAddIn`\-Klasse für das VSTO\-Add\-In. Weitere Information über diese Klasse finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Ausgeblendete Projektdateien, die nicht für eine direkte Bearbeitung vorgesehen sind. Weitere Informationen finden Sie unter [Ausgeblendete Projektdateien](#hiddenfiles).  
  
### Temporäre Zertifikate  
 Office\-Projekte umfassen auch ein temporäres Zertifikat mit dem Namen „*Projektname*\_TemporaryKey.pfx“. Dieses Zertifikat wird verwendet, um während der Entwicklung die Anwendung und die Bereitstellungsmanifeste für das Projekt zu signieren. Weitere Informationen finden Sie unter [Gewähren von Vertrauenswürdigkeit für Office-Projektmappen](../vsto/granting-trust-to-office-solutions.md) und [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).  
  
###  <a name="hiddenfiles"></a> Ausgeblendete Projektdateien  
 Mehrere Projektdateien werden standardmäßig ausgeblendet. Diese Dateien werden von Visual Studio generiert und unterscheiden sich anhand des Projekttyps. Um die ausgeblendeten Dateien anzuzeigen, klicken Sie im **Projektmappen\-Explorer** auf **Alle Dateien anzeigen**.  
  
 Ändern Sie die ausgeblendeten Projektdateien nicht. Eine direkte Änderung dieser Dateien wird nicht unterstützt und könnte das Projekt beschädigen. Bei bestimmten Änderungen im Dokument werden die ausgeblendeten Projektdateien neu generiert. Wenn Sie manuelle Änderungen an einer ausgeblendeten Projektdatei vornehmen, gehen diese Änderungen verloren, wenn die Datei erneut generiert wird.  
  
## Dokument\-Designer in Projekten auf Dokumentebene  
 Projekte auf Dokumentebene für Excel und Word stellen einen Designer bereit, der das Dokument hostet, das dem Projekt in Visual Studio zugeordnet ist. Mit dem Designer können Sie das Dokument ändern, ohne die Visual Studio\-Umgebung verlassen zu müssen.  
  
 Um im Designer ein Dokument zu öffnen, doppelklicken Sie im **Projektmappen\-Explorer** auf die Codedatei , die dem Dokument zugeordnet ist. Um beispielsweise das Arbeitsblatt **Blatt1** im Designer in einem Excel\-Projekt zu öffnen, doppelklicken Sie auf die **Blatt1**\-Codedatei.  
  
 Wenn Sie das Dokument im Designer ändern, können Sie die systemeigene Funktionalität der Office\-Anwendung nutzen. Sie können z. B. in dem Dokument oder in einem Arbeitsblatt Text eingeben, oder Sie können das Menüband verwenden, um Aufgaben wie das Hinzufügen einer Tabelle oder eines Diagramms auszuführen. Standardmäßig wird die Tastenkombinationszuordnung standardmäßig auf die Visual Studio\-Zuordnung festgelegt. Um stattdessen Office\-Tastenkombinationszuordnungen zu verwenden, ändern Sie die Einstellungen im Dialogfeld **Optionen** im Menü **Extras** unter dem Knoten **Microsoft Office\-Tastatureinstellungen**.  
  
### Steuerelemente in Dokumenten  
 Sie können *Hoststeuerelemente* und Windows Forms\-Steuerelemente aus der Visual Studio\-**Toolbox** auf die Dokumentdesignoberfläche ziehen. Hoststeuerelemente sind spezialisierte Versionen von Office\-Objekten, z. B. Word\-Inhaltssteuerelemente und Excel\-Bereiche, die in mit Visual Studio erstellten Office\-Projekten verwendet werden können. Hoststeuerelemente haben zusätzliche Funktionen, die in den entsprechenden Office\-Objekten nicht verfügbar sind, z. B. Datenbindung und zusätzliche Ereignisse.  
  
 Weitere Informationen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md) und [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
### Excel\-Arbeitsblätter und Arbeitsmappen im Designer  
 Wenn Sie im Designer ein Arbeitsblatt öffnen, können Sie das Arbeitsblatt genauso ändern, wie wenn es direkt in Excel geöffnet wäre. Nach dem Doppelklicken auf eine Arbeitsblattzelle wechselt diese in den Bearbeitungsmodus. Wenn Sie auf eine Zelle mit einem Hoststeuerelement doppelklicken, öffnet sich der Code\-Editor, und der Standardereignishandler für das Steuerelement wird von Visual Studio generiert. Um zu anderen Arbeitsblättern zu navigieren, können Sie auf die Arbeitsblattregisterkarten am unteren Rand des Designers klicken.  
  
 Wenn Sie die Arbeitsmappe im Designer öffnen, gibt es keine Designoberfläche. Die Entwurfsansicht für die Arbeitsmappe ist eine große Komponentenleiste, die den Designer ausfüllt.  
  
 Die Arbeitsmappe und die einzelnen Blätter in der Arbeitsmappe verfügen über eine zugeordnete Codedatei. Jede Codedatei enthält eine generierte *Hostelementklasse*, die die Arbeitsmappe oder das Blatt darstellt. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).  
  
### Word\-Dokumente im Designer  
 Wenn Sie das Dokument im Designer öffnen, können Sie es genauso ändern, wie wenn es direkt in Word geöffnet wäre. Wenn Sie auf ein Wort in dem Dokument doppelklicken, wird das Wort ausgewählt. Wenn sich das Wort allerdings innerhalb eines Hoststeuerelements befindet, wird der Code\-Editor geöffnet, und der Standardereignishandler des Steuerelements wird von Visual Studio generiert.  
  
 Das Dokument verfügt über eine zugeordnete Codedatei. Die Codedatei enthält eine generierte *Hostelementklasse*, die das Dokument darstellt. Weitere Informationen finden Sie unter [Dokumenthostelement](../vsto/document-host-item.md).  
  
### Vergleich von Entwurfsmodus und Laufzeitmodus  
 Dokumente werden in der Visual Studio\-Umgebung grundsätzlich im *Entwurfsmodus* geöffnet. Einige Aufgaben, z. B. das Ziehen eines Hoststeuerelements auf die Dokumentoberfläche, können nur im Entwurfsmodus ausgeführt werden.  
  
 Um ein Dokument im *Laufzeitmodus* anzuzeigen, müssen Sie die Anwendung und das Dokument außerhalb von Visual Studio öffnen. Wenn Sie das Projekt erstellen und ausführen, werden das Dokument und die Anwendung automatisch außerhalb von Visual Studio geöffnet.  
  
## Code\-Editor  
 Mithilfe des Code\-Editors können sie die sichtbaren Codedateien in der Projektmappe anzeigen und ändern. Diese Dateien enthalten den Code, in dem das Verhalten der Projektmappe definiert wird.  
  
 Weitere Informationen zum Code\-Editor finden Sie unter [Schreiben von Code im Code- und Text-Editor](../ide/writing-code-in-the-code-and-text-editor.md). Weitere Informationen zum Schreiben von Code in Office\-Projekten finden Sie unter [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md).  
  
## Eigenschaftenfenster  
 Im Fenster **Eigenschaften** werden Eigenschaften für Projektelemente angezeigt, die im **Projektmappen\-Explorer** ausgewählt werden, sowie für Benutzeroberflächenelemente, die im Designer ausgewählt werden, z. B. Steuerelemente oder das Dokument in einem Projekt auf Dokumentebene. Einige der Eigenschaften sind spezifisch für die Anwendung und das Dokument, andere Eigenschaften sind für alle Projekte gleich.  
  
## Datenquellenfenster  
 Sie können das Fenster **Datenquellen** in Office\-Projekten auf Dokumentebene verwenden, um eine Datenquelle in das Dokument zu ziehen und ein Steuerelement zu erstellen, das an die Datenquelle gebunden ist. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../Topic/Binding%20controls%20to%20data%20in%20Visual%20Studio.md).  
  
## Siehe auch  
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)   
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md)  
  
  