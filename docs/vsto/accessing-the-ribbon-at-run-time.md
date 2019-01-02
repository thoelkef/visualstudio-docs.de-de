---
title: Zugriff auf das Menüband zur Laufzeit
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a20297ee0d60173cbd0513f3d34e12f12388bdb
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304622"
---
# <a name="access-the-ribbon-at-runtime"></a>Zugriff auf das Menüband zur Laufzeit
  Sie können Code zum Einblenden, Ausblenden und Ändern des Menübands schreiben und Benutzern das Ausführen des Codes von Steuerelementen in einem benutzerdefinierten Aufgabenbereich, Aktionsbereich oder Outlook-Formularbereich ermöglichen.  

 Sie können mit der `Globals`-Klasse auf das Menüband zugreifen. Bei Outlook-Projekten können Sie auf die Menübänder zugreifen, die in einem bestimmten Outlook-Inspektor- oder Outlook-Explorer-Fenster angezeigt werden.  

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Zugriff auf das Menüband mithilfe der Globals-Klasse  
 Sie können die `Globals`-Klasse verwenden, um von einer beliebigen Stelle im Projekt auf das Menüband in einem Projekt auf Dokumentebene oder in einem VSTO-Add-In-Projekt zuzugreifen.  

 Weitere Informationen zu den `Globals` Klasse, finden Sie unter [Global den Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  

 Im folgenden Beispiel wird die`Globals`-Klasse für den Zugriff auf ein benutzerdefiniertes Menüband mit der Bezeichnung `Ribbon1` und zum Festlegen des Texts verwendet, der in einem Kombinationsfeld im Menüband für `Hello World` angezeigt wird.  

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Zugriff auf eine Auflistung von Menübändern, die in einem bestimmten Outlook-Inspektor-Fenster angezeigt werden.  
 Sie können eine Auflistung von Menübändern, die in Outlook angezeigt werden zugreifen *Inspektoren*. Ein Inspektor ist ein Fenster, das in Outlook geöffnet wird, wenn Benutzer bestimmte Aufgaben ausführen, z. B. E-Mails verfassen. Um auf das Menüband eines Inspektor-Fensters zuzugreifen, rufen Sie die `Ribbons`-Eigenschaft der `Globals`-Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Inspector>-Objekt, das den Inspektor darstellt.  

 Im folgenden Beispiel wird die Menübandauflistung des Inspektors abgerufen, der gerade den Fokus besitzt. In diesem Beispiel wird dann auf ein Menüband mit der Bezeichnung `Ribbon1` zugegriffen und der Text festgelegt, der in einem Kombinationsfeld im Menüband für `Hello World` angezeigt wird.  

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Zugriff auf eine Auflistung von Menübändern, die für einen bestimmten Outlook-Explorer angezeigt werden.  
 Sie erreichen eine Auflistung von Menübändern, die in Outlook angezeigt werden *Explorer*. Ein Explorer ist die Haupt-Benutzeroberfläche (UI) der Anwendung für eine Instanz von Outlook. Um auf das Menüband eines Explorer-Fensters zuzugreifen, rufen Sie die `Ribbons`-Eigenschaft der `Globals`-Klasse auf und übergeben ein <xref:Microsoft.Office.Interop.Outlook.Explorer>-Objekt, das den Explorer darstellt.  

 Im folgenden Beispiel wird die Menübandauflistung des Explorers abgerufen, der gerade den Fokus besitzt. In diesem Beispiel wird dann auf ein Menüband mit der Bezeichnung `Ribbon1` zugegriffen und der Text festgelegt, der in einem Kombinationsfeld im Menüband für `Hello World` angezeigt wird.  

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  

## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-Designer](../vsto/ribbon-designer.md)   
 [Menüband-XML](../vsto/ribbon-xml.md)   
 [Übersicht über das Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Zugriff auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)  
