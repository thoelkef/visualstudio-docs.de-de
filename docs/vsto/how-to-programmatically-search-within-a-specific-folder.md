---
title: "Gewusst wie: Programmgesteuerte Suche in einem bestimmten Ordner"
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
  - "Outlook-Ordner [Office-Entwicklung in Visual Studio], Suchen"
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Gewusst wie: Programmgesteuerte Suche in einem bestimmten Ordner
  In diesem Codebeispiel werden die `Find`\-Methode und die `FindNext`\-Methode verwendet, um im Feld Betreff der im **Posteingang** befindlichen E\-Mail\-Nachrichten nach Text zu suchen.  Diese Methode verwendet einen Zeichenfolgenfilter, der alle `Subject`\-Texte findet, die mit dem Buchstaben T anfangen.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Beispiel  
 [!code-csharp[Trin_OL_SearchFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchFolder/CS/thisaddin.cs#1)]  
  
## Siehe auch  
 [Arbeiten mit Ordnern](../vsto/working-with-folders.md)   
 [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  