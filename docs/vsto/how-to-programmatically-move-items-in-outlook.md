---
title: "Gewusst wie: Programmgesteuertes Verschieben von Elementen in Outlook"
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
  - "Outlook-Ordner [Office-Entwicklung in Visual Studio], Verschieben von Elementen"
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Programmgesteuertes Verschieben von Elementen in Outlook
  In diesem Beispiel werden ungelesene E\-Mail\-Nachrichten aus dem **Posteingang** in einen Ordner mit dem Namen **Test** verschoben.  Es werden jedoch nur Nachrichten verschoben, die das Wort **Test** im Feld `Subject` aufweisen.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Beispiel  
 [!code-csharp[Trin_OL_MoveItems#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_MoveItems/CS/thisaddin.cs#1)]  
  
## Kompilieren des Codes  
 Dieses Beispiel setzt Folgendes voraus:  
  
-   Ein Outlook\-E\-Mail\-Ordner mit dem Namen **Test**.  
  
-   Eine E\-Mail\-Nachricht, die mit dem Wort **Test** im Feld `Subject` ankommt.  
  
## Siehe auch  
 [Arbeiten mit Ordnern](../vsto/working-with-folders.md)   
 [Gewusst wie: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Gewusst wie: Programmgesteuerte Suche in einem bestimmten Ordner](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Gewusst wie: Programmgesteuertes Ausführen von Aktionen beim Empfang einer E-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  