---
title: "Gewusst wie: Programmgesteuertes Bestimmen des aktuellen Outlook-Elements | Microsoft Docs"
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
  - "E-Mail [Office-Entwicklung in Visual Studio], Aktuelles Element"
  - "E-Mail-Elemente [Office-Entwicklung in Visual Studio], Aktuell"
  - "Outlook [Office-Entwicklung in Visual Studio], Aktuelles Element"
  - "SelectionChange-Ereignis"
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Gewusst wie: Programmgesteuertes Bestimmen des aktuellen Outlook-Elements
  In diesem Beispiel wird das Explorer.SelectionChange\-Ereignis verwendet, um den Namen des aktuellen Ordners und einige Informationen über das ausgewählte Element anzuzeigen.  Anschließend wird das ausgewählte Element angezeigt.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Beispiel  
 [!code-csharp[Trin_OL_CurrentItem#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/CS/thisaddin.cs#1)]
 [!code-vb[Trin_OL_CurrentItem#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/VB/thisaddin.vb#1)]  
  
## Kompilieren des Codes  
 Dieses Beispiel setzt Folgendes voraus:  
  
-   Termin\-, Kontakt\- und E\-Mail\-Elemente in Microsoft Office Outlook.  
  
## Siehe auch  
 [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Gewusst wie: Programmgesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  