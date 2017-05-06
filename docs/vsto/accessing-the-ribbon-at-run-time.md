---
title: "Zugreifen auf die Multifunktionsleiste zur Laufzeit"
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
  - "Globals-Klasse, Menüband"
  - "Menüband [Office-Entwicklung in Visual Studio], Aufrufen"
  - "RibbonManager-Klasse"
ms.assetid: 8a7c7c6d-1a18-4d6b-98ee-e483d41f0cd8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Zugreifen auf die Multifunktionsleiste zur Laufzeit
  Sie können Code zum Einblenden, Ausblenden und Ändern des Menübands schreiben und Benutzern das Ausführen des Codes von Steuerelementen in einem benutzerdefinierten Aufgabenbereich, Aktionsbereich oder Outlook\-Formularbereich ermöglichen.  
  
 Sie können mit der `Globals`\-Klasse auf das Menüband zugreifen.  Bei Outlook\-Projekten können Sie auf die Menübänder zugreifen, die in einem bestimmten Outlook\-Inspektor\- oder Outlook\-Explorer\-Fenster angezeigt werden.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Zugreifen auf das Menüband mithilfe der Globals\-Klasse  
 Sie können die `Globals`\-Klasse verwenden, um von einer beliebigen Stelle im Projekt auf das Menüband in einem Projekt auf Dokumentebene oder in einem VSTO\-Add\-In\-Projekt zuzugreifen.  
  
 Weitere Informationen zur `Globals`\-Klasse finden Sie unter [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  
  
 Im folgenden Beispiel wird die`Globals`\-Klasse für den Zugriff auf ein benutzerdefiniertes Menüband mit der Bezeichnung `Ribbon1` und zum Festlegen des Texts verwendet, der in einem Kombinationsfeld im Menüband für `Hello World` angezeigt wird.  
  
 [!code-csharp[Trin_Outlook_FR_Access#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#4)]
 [!code-vb[Trin_Outlook_FR_Access#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#4)]  
  
## Zugreifen auf eine Auflistung von Menübändern, die in einem bestimmten Outlook\-Inspektor\-Fenster angezeigt werden  
 Sie können auf eine Auflistung von Menübändern zugreifen, die in *Inspektoren* von Outlook angezeigt werden.  Ein Inspektor ist ein Fenster, das in Outlook geöffnet wird, wenn Benutzer bestimmte Aufgaben ausführen, z. B. E\-Mails verfassen.  Um auf das Menüband eines Inspektor\-Fensters zuzugreifen, rufen Sie die `Ribbons`\-Eigenschaft der `Globals`\-Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekt, das den Inspektor darstellt.  
  
 Im folgenden Beispiel wird die Menübandauflistung des Inspektors abgerufen, der gerade den Fokus besitzt.  In diesem Beispiel wird dann auf ein Menüband mit der Bezeichnung `Ribbon1` zugegriffen und der Text festgelegt, der in einem Kombinationsfeld im Menüband für `Hello World` angezeigt wird.  
  
 [!code-csharp[Trin_Outlook_FR_Access#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#5)]
 [!code-vb[Trin_Outlook_FR_Access#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#5)]  
  
## Zugreifen auf eine Auflistung von Menübändern, die in einem bestimmten Outlook\-Explorer angezeigt werden  
 Sie können auf eine Auflistung von Menübändern zugreifen, die in einem Outlook\-*Explorer* angezeigt werden.  Ein Explorer ist die Haupt\-Benutzeroberfläche \(UI\) der Anwendung für eine Instanz von Outlook.  Um auf das Menüband eines Explorer\-Fensters zuzugreifen, rufen Sie die `Ribbons`\-Eigenschaft der `Globals`\-Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Explorer>\-Objekt, das den Explorer darstellt.  
  
 Im folgenden Beispiel wird die Menübandauflistung des Explorers abgerufen, der gerade den Fokus besitzt.  In diesem Beispiel wird dann auf ein Menüband mit der Bezeichnung `Ribbon1` zugegriffen und der Text festgelegt, der in einem Kombinationsfeld im Menüband für `Hello World` angezeigt wird.  
  
 [!code-csharp[Trin_Outlook_FR_Access#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#6)]
 [!code-vb[Trin_Outlook_FR_Access#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#6)]  
  
## Siehe auch  
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)   
 [Multifunktionsleisten-Objektmodellübersicht](../vsto/ribbon-object-model-overview.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente in einer Multifunktionsleiste zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Anpassen einer Multifunktionsleiste in Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Zugreifen auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)  
  
  