---
title: "Anpassen einer Multifunktionsleiste in Outlook | Microsoft Docs"
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
  - "Benutzerdefiniertes Menüband, Informationen zum Anpassen der Multifunktionsleiste"
  - "Anpassen des Menübands, Informationen zum Anpassen der Multifunktionsleiste"
  - "Inspektoren [Office-Entwicklung in Visual Studio]"
  - "Outlook [Office-Entwicklung in Visual Studio], Menüband"
  - "Menüband [Office-Entwicklung in Visual Studio], Outlook"
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Anpassen einer Multifunktionsleiste in Outlook
  Beim Anpassen des Menübands in Microsoft Office Outlook müssen Sie berücksichtigen, wo das benutzerdefinierte Menüband in der Anwendung angezeigt wird.  Outlook zeigt das Menüband in der Benutzeroberfläche der Hauptanwendung und in Fenstern an, die geöffnet werden, wenn Benutzer bestimmte Aufgaben ausführen, z. B. eine E\-Mail erstellen.  Diese Anwendungsfenster werden als Inspektoren bezeichnet.  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Gewusst wie: Verwenden des Menüband\-Designers zum Anpassen des Menübands in Outlook](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Hinzufügen eines benutzerdefinierten Menübands zur Benutzeroberfläche der Hauptanwendung  
 Die Benutzeroberfläche der Hauptanwendung in Outlook ist der Explorer.  Bei Verwendung des Elements **Menüband \(Visueller Designer\)** können Sie dem Explorer ein Menüband hinzufügen, indem Sie im Fenster **Eigenschaften** auf die **RibbonType**\-Eigenschaft des Menübands klicken und dann **Microsoft.Outlook.Explorer** auswählen.  
  
## Zuordnen eines Menübands zu einem Inspektor  
 Sie identifizieren den anzupassenden Inspektor durch Angabe des Menübandtyps, der der Nachrichtenklasse des Inspektors entspricht.  
  
 Bei Verwendung des Elements **Menüband \(Visueller Designer\)** klicken Sie auf die **RibbonType**\-Eigenschaft des Menübands im Fenster **Eigenschaften**, und wählen Sie dann mindestens eine Menüband\-ID aus der Werteliste aus.  
  
 Sie können einem Projekt mehrere Menübänder hinzufügen.  Wenn sich mehrere Menübänder eine Menüband\-ID teilen, überschreiben Sie die CreateRibbonExtensibilityObject\-Methode in der `ThisAddin`\-Klasse des Projekts, um anzugeben, welches Menüband zur Laufzeit angezeigt werden soll.  Weitere Informationen finden Sie unter [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md).  Weitere Informationen zu den einzelnen Menübandtypen finden Sie im technischen Artikel [Anpassen des Menübands in Outlook 2007](http://msdn.microsoft.com/de-de/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## Angeben des Menübandtyps mithilfe der Menüband\-XML  
 Bei Verwendung des Elements **Menüband \(XML\)** überprüfen Sie den Wert des *ribbonID*\-Parameters in der <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>\-Methode, und geben Sie das entsprechende Menüband zurück.  
  
 Die <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>\-Methode wird automatisch von Visual Studio in der Menüband\-Codedatei generiert.  Der *ribbonID*\-Parameter ist eine Zeichenfolge, die den Explorer oder einen bestimmten Inspektortyp identifiziert.  Eine vollständige Liste der möglichen Werte des *ribbonID*\-Parameters finden Sie im technischen Artikel [Anpassen des Menübands in Outlook 2007](http://msdn.microsoft.com/de-de/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Menüband nur im `Microsoft.Outlook.Mail.Compose`\-Inspektor angezeigt wird.  Dies ist der Inspektor, der geöffnet wird, wenn ein Benutzer eine neue E\-Mail erstellt.  Das anzuzeigende Menüband wird in der `GetResourceText()`\-Methode angegeben, die in der **Ribbon**\-Klasse generiert wird.  Weitere Informationen zur **Ribbon**\-Klasse finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#1)]  
  
## Siehe auch  
 [Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)  
  
  