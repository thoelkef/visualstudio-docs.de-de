---
title: "Anpassen eines Men&#252;bands f&#252;r InfoPath | Microsoft Docs"
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
  - "InfoPath [Office-Entwicklung in Visual Studio], Menüband"
  - "Menüband [Office-Entwicklung in Visual Studio], InfoPath"
ms.assetid: 498c6457-679a-46f2-939f-c0597a17b7ec
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Anpassen eines Men&#252;bands f&#252;r InfoPath
  Beim Anpassen des Menübands in Microsoft Office InfoPath müssen Sie berücksichtigen, wo das benutzerdefinierte Menüband in der Anwendung angezeigt wird.[!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] kann das Menüband in den folgenden drei Typen von InfoPath\-Anwendungsfenstern anzeigen:  
  
-   Fenster, in denen eine Formularvorlage angezeigt wird, die im Entwurfsmodus geöffnet ist.  
  
-   Fenster, in denen ein Formular angezeigt wird, das auf einer Formatvorlage basiert.  
  
-   Im Seitenansichtsfenster.  
  
 **Betrifft:** Die Informationen in diesem Thema betreffen VSTO\-Add\-In\-Projekte für InfoPath 2010. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Benutzer und Designer öffnen eine Formularvorlage im Entwurfsmodus, um die Darstellung und das Layout der Vorlage zu ändern. Benutzer öffnen Formulare, die auf einer Formularvorlage basieren, um Inhalte hinzuzufügen.  
  
 Im Seitenansichtsfenster können Designer und Benutzer, die Seiten eines Formulars oder einer Formularvorlage vor dem Drucken in der Vorschau anzeigen.  
  
> [!NOTE]  
>  Die Registerkarte **Add\-Ins** wird im Seitenansichtsfenster nicht angezeigt. Wenn eine benutzerdefinierte Registerkarte im Seitenansichtsfenster angezeigt werden soll, stellen Sie sicher, dass die **OfficeId** \-Eigenschaft der Registerkarte nicht auf **TabAddIns** festgelegt ist.  
  
 Sie müssen den Menübandtyp jedes Fensters angeben, in denen das Menüband angezeigt werden soll.  
  
## Angeben des Menübandtyps im Menüband\-Designer  
 Bei Verwendung des Elements **Menüband \(Visual Designer\)** klicken Sie auf die **RibbonType** \-Eigenschaft des Menübands im Fenster **Eigenschaften**, und wählen Sie dann eine der in der folgenden Tabelle beschriebenen Menüband\-IDs aus.  
  
|Menüband\-ID|Fenster, in dem das Menüband angezeigt wird, wenn Sie das Projekt ausführen|  
|------------------|---------------------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Fenster, in denen eine Formularvorlage angezeigt wird, die im Entwurfsmodus geöffnet ist.|  
|**Microsoft.InfoPath.Editor**|Fenster, in denen ein Formular angezeigt wird, das auf einer Formatvorlage basiert.|  
|**Microsoft.InfoPath.PrintPreview**|Im Seitenansichtsfenster.|  
  
 Sie können einem Projekt mehrere Menübänder hinzufügen. Wenn sich mehrere Menübänder eine Menüband\-ID teilen, überschreiben Sie die CreateRibbonExtensibilityObject \-Methode in der `ThisAddin` \-Klasse des Projekts, um anzugeben, welches Menüband zur Laufzeit ausgeführt werden soll. Weitere Informationen finden Sie unter [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md).  
  
## Angeben des Menübandtyps mithilfe der Menüband\-XML  
 Bei Verwendung des Elements **Menüband \(XML\)** überprüfen Sie den Wert des *ribbonID* \-Parameters in der <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> \-Methode, und geben Sie das entsprechende Menüband zurück.  
  
 Die <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A>\-Methode wird automatisch von Visual Studio in der Menüband\-Codedatei generiert. Der *ribbonID* \-Parameter ist eine Zeichenfolge, die den Typ des InfoPath\-Fensters identifiziert, das geöffnet wird, angibt.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Menüband nur in einem Fenster angezeigt wird, in dem eine Formularvorlage im Entwurfsmodus angezeigt wird. Das anzuzeigende Menüband wird in der `GetResourceText()`\-Methode angegeben, die in der Menübandklasse generiert wird. Weitere Informationen zur Menübandklasse finden Sie unter [Multifunktionsleisten-XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_ribboninfopathbasic/cs/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_ribboninfopathbasic/vb/ribbon.vb#1)]  
  
## Siehe auch  
 [Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Multifunktionsleisten-XML](../vsto/ribbon-xml.md)  
  
  