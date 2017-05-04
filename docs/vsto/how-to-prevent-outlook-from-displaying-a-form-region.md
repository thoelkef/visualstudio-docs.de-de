---
title: "Gewusst wie: Verhindern der Anzeige eines Formularbereichs in Outlook | Microsoft Docs"
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
  - "Abbrechen der Anzeige von Formularbereichen"
  - "Formularbereiche [Office-Entwicklung in Visual Studio], Abbrechen der Anzeige"
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Gewusst wie: Verhindern der Anzeige eines Formularbereichs in Outlook
  In manchen Situationen möchten Sie möglicherweise nicht, dass Microsoft Office Outlook einen bestimmten Formularbereich für ein bestimmtes Element anzeigt.  Wenn ein Kontaktelement keine Geschäftsadresse enthält, können Sie die Anzeige eines Formularbereichs verhindern, der den Standort des Geschäfts auf einer Karte zeigt.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### So wird Outlook am Anzeigen eines Formularbereichs gehindert  
  
1.  Öffnen Sie die Codedatei für den zu ändernden Formularbereich.  
  
2.  Erweitern Sie den Codebereich **Formularbereichsfactory**.  
  
3.  Fügen Sie dem  `FormRegionInitializing`\-Ereignishandler Code hinzu, mit dem die <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>\-Eigenschaft der <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>\-Klasse auf **true** festgelegt wird.  
  
 Beinhaltet das Kontaktelement in diesem Beispiel keine Adresse, wird die <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>\-Eigenschaft auf **true** festgelegt, und der Formularbereich wird nicht angezeigt.  
  
## Beispiel  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
## Siehe auch  
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  