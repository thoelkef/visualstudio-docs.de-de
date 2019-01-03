---
title: Anpassen eines Menübands für InfoPath
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c69ef50662bd1b98e896d1b8d3933d23be26123c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837263"
---
# <a name="customize-a-ribbon-for-infopath"></a>Anpassen eines Menübands für InfoPath
  Beim Anpassen des Menübands in Microsoft Office InfoPath müssen Sie berücksichtigen, wo das benutzerdefinierte Menüband in der Anwendung angezeigt wird. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] kann das Menüband in den folgenden drei Typen von InfoPath-Anwendungsfenstern anzeigen:  
  
- Fenster, in denen eine Formularvorlage angezeigt wird, die im Entwurfsmodus geöffnet ist.  
  
- Fenster, in denen ein Formular angezeigt wird, das auf einer Formatvorlage basiert.  
  
- Im Seitenansichtsfenster.  
  
  **Gilt für:** Die Informationen in diesem Thema betreffen VSTO-Add-in-Projekte für InfoPath 2010. Weitere Informationen finden Sie unter [verfügbare Funktionen nach Office-Anwendung und Projekt Typ](../vsto/features-available-by-office-application-and-project-type.md).  
  
  Benutzer und Designer öffnen eine Formularvorlage im Entwurfsmodus, um die Darstellung und das Layout der Vorlage zu ändern. Benutzer öffnen Formulare, die auf einer Formularvorlage basieren, um Inhalte hinzuzufügen.  
  
  Im Seitenansichtsfenster können Designer und Benutzer, die Seiten eines Formulars oder einer Formularvorlage vor dem Drucken in der Vorschau anzeigen.  
  
> [!NOTE]  
>  Die Registerkarte **Add-Ins** wird im Seitenansichtsfenster nicht angezeigt. Wenn eine benutzerdefinierte Registerkarte im Seitenansichtsfenster angezeigt werden soll, stellen Sie sicher, dass die **OfficeId** -Eigenschaft der Registerkarte nicht auf **TabAddIns**festgelegt ist.  
  
 Sie müssen den Menübandtyp jedes Fensters angeben, in denen das Menüband angezeigt werden soll.  
  
## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Angeben des Menübandtyps im Menüband-designer  
 Bei Verwendung der **Menüband (visueller Designer)** Element, klicken Sie auf die **RibbonType** -Eigenschaft des Menübands in die **Eigenschaften** Fenster, und wählen Sie dann eine Menüband-IDs in der folgenden Tabelle beschrieben.  
  
|Menüband-ID|Fenster, in dem das Menüband angezeigt wird, wenn Sie das Projekt ausführen|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Fenster, in denen eine Formularvorlage angezeigt wird, die im Entwurfsmodus geöffnet ist.|  
|**Microsoft.InfoPath.Editor**|Fenster, in denen ein Formular angezeigt wird, das auf einer Formatvorlage basiert.|  
|**Microsoft.InfoPath.PrintPreview**|Im Seitenansichtsfenster.|  
  
 Sie können einem Projekt mehrere Menübänder hinzufügen. Wenn sich mehrere Menübänder eine Menüband-ID teilen, überschreiben Sie die `CreateRibbonExtensibilityObject` -Methode in der `ThisAddin` -Klasse des Projekts, um anzugeben, welches Menüband zur Laufzeit ausgeführt werden soll. Weitere Informationen finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Angeben des Menübandtyps mithilfe des Menüband-XML  
 Bei Verwendung des Elements **Menüband (XML)** überprüfen Sie den Wert des *ribbonID* -Parameters in der <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> -Methode, und geben Sie das entsprechende Menüband zurück.  
  
 Die <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> -Methode wird automatisch von Visual Studio in der Menüband-Codedatei generiert. Der *ribbonID* -Parameter ist eine Zeichenfolge, die den Typ des InfoPath-Fensters identifiziert, das geöffnet wird, angibt.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Menüband nur in einem Fenster angezeigt wird, in dem eine Formularvorlage im Entwurfsmodus angezeigt wird. Das anzuzeigende Menüband wird in der `GetResourceText()` -Methode angegeben, die in der Menübandklasse generiert wird. Weitere Informationen zur Menübandklasse finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>Siehe auch  
 [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-designer](../vsto/ribbon-designer.md)   
 [Ribbon XML](../vsto/ribbon-xml.md)  
