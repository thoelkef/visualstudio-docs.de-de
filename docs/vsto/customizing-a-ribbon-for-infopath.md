---
title: "Anpassen eines Menübands für InfoPath | Microsoft Docs"
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
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
ms.assetid: 498c6457-679a-46f2-939f-c0597a17b7ec
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3f4612b3e8dc272b0f51bae80d66d8afe97938e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-a-ribbon-for-infopath"></a>Anpassen eines Menübands für InfoPath
  Beim Anpassen des Menübands in Microsoft Office InfoPath müssen Sie berücksichtigen, wo das benutzerdefinierte Menüband in der Anwendung angezeigt wird. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] kann das Menüband in den folgenden drei Typen von InfoPath-Anwendungsfenstern anzeigen:  
  
-   Fenster, in denen eine Formularvorlage angezeigt wird, die im Entwurfsmodus geöffnet ist.  
  
-   Fenster, in denen ein Formular angezeigt wird, das auf einer Formatvorlage basiert.  
  
-   Im Seitenansichtsfenster.  
  
 **Betrifft:** Die Informationen in diesem Thema betreffen VSTO-Add-In-Projekte für InfoPath 2010. Weitere Informationen finden Sie unter [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Benutzer und Designer öffnen eine Formularvorlage im Entwurfsmodus, um die Darstellung und das Layout der Vorlage zu ändern. Benutzer öffnen Formulare, die auf einer Formularvorlage basieren, um Inhalte hinzuzufügen.  
  
 Im Seitenansichtsfenster können Designer und Benutzer, die Seiten eines Formulars oder einer Formularvorlage vor dem Drucken in der Vorschau anzeigen.  
  
> [!NOTE]  
>  Die Registerkarte **Add-Ins** wird im Seitenansichtsfenster nicht angezeigt. Wenn eine benutzerdefinierte Registerkarte im Seitenansichtsfenster angezeigt werden soll, stellen Sie sicher, dass die **OfficeId** -Eigenschaft der Registerkarte nicht auf **TabAddIns**festgelegt ist.  
  
 Sie müssen den Menübandtyp jedes Fensters angeben, in denen das Menüband angezeigt werden soll.  
  
## <a name="specifying-the-ribbon-type-in-the-ribbon-designer"></a>Angeben des Menübandtyps im Menüband-Designer  
 Bei Verwendung des Elements **Menüband (Visual Designer)** klicken Sie auf die **RibbonType** -Eigenschaft des Menübands im Fenster **Eigenschaften** , und wählen Sie dann eine der in der folgenden Tabelle beschriebenen Menüband-IDs aus.  
  
|Menüband-ID|Fenster, in dem das Menüband angezeigt wird, wenn Sie das Projekt ausführen|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Fenster, in denen eine Formularvorlage angezeigt wird, die im Entwurfsmodus geöffnet ist.|  
|**Microsoft.InfoPath.Editor**|Fenster, in denen ein Formular angezeigt wird, das auf einer Formatvorlage basiert.|  
|**Microsoft.InfoPath.PrintPreview**|Im Seitenansichtsfenster.|  
  
 Sie können einem Projekt mehrere Menübänder hinzufügen. Wenn mehrere Menübänder eine Menüband-ID Teilen, überschreiben Sie die CreateRibbonExtensibilityObject-Methode in der `ThisAddin` -Klasse des Projekts an, welches Menüband zur Laufzeit angezeigt. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Angeben des Menübandtyps mithilfe der Menüband-XML  
 Bei Verwendung des Elements **Menüband (XML)** überprüfen Sie den Wert des *ribbonID* -Parameters in der <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> -Methode, und geben Sie das entsprechende Menüband zurück.  
  
 Die <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> -Methode wird automatisch von Visual Studio in der Menüband-Codedatei generiert. Der *ribbonID* -Parameter ist eine Zeichenfolge, die den Typ des InfoPath-Fensters identifiziert, das geöffnet wird, angibt.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Menüband nur in einem Fenster angezeigt wird, in dem eine Formularvorlage im Entwurfsmodus angezeigt wird. Das anzuzeigende Menüband wird in der `GetResourceText()` -Methode angegeben, die in der Menübandklasse generiert wird. Weitere Informationen zur Menübandklasse finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-Designer](../vsto/ribbon-designer.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)  
  
  