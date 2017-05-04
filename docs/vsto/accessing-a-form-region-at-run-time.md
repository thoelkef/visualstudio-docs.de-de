---
title: "Zugreifen auf einen Formularbereich zur Laufzeit | Microsoft Docs"
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
  - "Inspektoren [Office-Entwicklung in Visual Studio]"
  - "Explorer [Office-Entwicklung in Visual Studio]"
  - "Formularbereiche [Office-Entwicklung in Visual Studio], Zugriff zur Laufzeit"
ms.assetid: 58eaa9e0-acba-4a13-a6dd-b7e37a38156e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Zugreifen auf einen Formularbereich zur Laufzeit
  
  
|Betrifft|  
|--------------|  
|Die Informationen in diesem Thema gelten nur für die angegebenen Projekttypen und Versionen von Microsoft Office. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Projekttyp:**<br /><br /> -   VSTO\-Add\-In\-Projekte<br /><br /> **Microsoft Office\-Version**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  
  
 Verwenden Sie die `Globals`\-Klasse, um überall im Outlook\-Projekt auf Formularbereiche zuzugreifen. Weitere Informationen zur `Globals`\-Klasse finden Sie unter [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Zugreifen auf Formularbereiche, die in einem bestimmten Outlook\-Inspektor\-Fenster angezeigt werden  
 Um auf alle Formularbereiche in einem bestimmten Inspektor\-Fenster zuzugreifen, rufen Sie die `FormRegions`\-Eigenschaft der `Globals`\-Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekt, das den Inspektor darstellt.  
  
 Im folgenden Beispiel wird die Auflistung von Formularbereichen abgerufen, die in dem Inspektor angezeigt werden, der gerade den Fokus besitzt. In diesem Beispiel wird dann auf einen Formularbereich in der Auflistung mit dem Namen `formRegion1` zugegriffen, und der Text, der in einem Textfeld angezeigt wird, wird auf `Hello World` festgelegt.  
  
 [!code-csharp[Trin_Outlook_FR_Access#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_Outlook_FR_Access#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#2)]  
  
## Zugreifen auf Formularbereiche, die in einem bestimmten Outlook\-Explorer\-Fenster angezeigt werden  
 Um auf alle Formularbereiche in einem bestimmten Explorer\-Fenster zuzugreifen, rufen Sie die `FormRegions`\-Eigenschaft der `Globals`\-Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Explorer>\-Objekt, das den Explorer darstellt.  
  
 Im folgenden Beispiel wird die Auflistung von Formularbereichen abgerufen, die in dem Explorer angezeigt werden, der gerade den Fokus besitzt. In diesem Beispiel wird dann auf einen Formularbereich in der Auflistung mit dem Namen `formRegion1` zugegriffen, und der Text, der in einem Textfeld angezeigt wird, wird auf `Hello World` festgelegt.  
  
 [!code-csharp[Trin_Outlook_FR_Access#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#3)]
 [!code-vb[Trin_Outlook_FR_Access#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#3)]  
  
## Zugreifen auf alle Formularbereiche  
 Um auf alle Formularbereiche zuzugreifen, die in allen Explorern und Inspektoren angezeigt werden, rufen Sie die `FormRegions`\-Eigenschaft der `Globals`\-Klasse auf.  
  
 Im folgenden Beispiel wird die Auflistung von Formularbereichen abgerufen, die in allen Explorern und Inspektoren angezeigt werden. In diesem Beispiel wird dann auf einen Formularbereich mit dem Namen `formRegion1` zugegriffen, und der Text, der in einem Textfeld angezeigt wird, wird auf `Hello World` festgelegt.  
  
 [!code-csharp[Trin_Outlook_FR_Access#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_Outlook_FR_Access#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#1)]  
  
## Zugreifen auf Steuerelemente in einem Formularbereich  
 Für den Zugriff auf Steuerelemente in einem Formularbereich mithilfe der `Globals`\-Klasse müssen Sie die Steuerelemente für Code außerhalb der Formularbereich\-Codedatei zugänglich machen.  
  
### Im Formularbereich\-Designer entworfene Formularbereiche  
 Ändern Sie für C\# den Modifizierer für jedes Steuerelement, auf das Sie zugreifen möchten. Zu diesem Zweck wählen Sie jedes Steuerelement im Formularbereich\-Designer aus und ändern im Fenster **Eigenschaften** die **Modifiers**\-Eigenschaft in **Internal** oder **public**. Wenn Sie die **Modifier**\-Eigenschaft von `textBox1` beispielsweise in **Internal** ändern, können Sie durch Eingabe von `Globals.FormRegions.FormRegion1.textBox1` auf `textBox1` zugreifen.  
  
 Für Visual Basic müssen Sie den Modifizierer nicht ändern.  
  
### Importierte Formularbereiche  
 Beim Importieren eines Formularbereichs, der in Outlook entworfen wurde, wird der Zugriffsmodifizierer jedes Steuerelements im Formularbereich privat. Da der Formularbereich\-Designer nicht zum Ändern eines importierten Formularbereichs verwendet werden kann, besteht keine Möglichkeit, den Modifizierer eines Steuerelements im Fenster **Eigenschaften** zu ändern.  
  
 Um den Zugriff auf ein Steuerelement von außerhalb der Formularbereich\-Codedatei zu ermöglichen, erstellen Sie in der Formularbereich\-Codedatei eine Eigenschaft, um dieses Steuerelement zurückzugeben.  
  
 Weitere Informationen zum Erstellen von Eigenschaften in C\# finden Sie unter [Gewusst wie: Deklarieren und Verwenden von Lese-&#47;Schreibeigenschaften &#40;C&#35;-Programmierhandbuch&#41;](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20(C%23%20Programming%20Guide).md).  
  
 Weitere Informationen zum Erstellen von Eigenschaften in Visual Basic finden Sie unter [NICHT IM BUILD: Gewusst wie: Hinzufügen von Feldern und Eigenschaften zu einer Klasse](http://msdn.microsoft.com/de-de/ae53f61b-3abc-413e-8931-703c5f5e8fc2).  
  
## Siehe auch  
 [Richtlinien zum Erstellen von Outlook-Formularbereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Benutzerdefinierte Aktionen in Outlook-Formularbereichen](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Gewusst wie: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  