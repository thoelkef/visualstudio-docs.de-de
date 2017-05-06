---
title: "Gewusst wie: Programmgesteuertes Zuordnen einer Webseite zu einem Outlook-Ordner"
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
  - "Ordner [Office-Entwicklung in Visual Studio], Webseiten und"
  - "Outlook [Office-Entwicklung in Visual Studio], An Ordner angefügte Webseiten"
  - "Webseiten [Office-Entwicklung in Visual Studio], Outlook-Ordner"
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Gewusst wie: Programmgesteuertes Zuordnen einer Webseite zu einem Outlook-Ordner
  In diesem Beispiel wird in Microsoft Office Outlook nach einem Ordner mit dem Namen `HtmlView` gesucht.  Wenn der Ordner noch nicht vorhanden ist, erstellt der Code den Ordner und weist diesem eine Webseite zu.  Ist der Ordner bereits vorhanden, wird der Ordnerinhalt angezeigt.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Beispiel  
 [!code-csharp[Trin_OL_HTMLFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_HTMLFolder/CS/thisaddin.cs#1)]  
  
## Siehe auch  
 [Arbeiten mit Ordnern](../vsto/working-with-folders.md)   
 [Gewusst wie: Programmgesteuertes Abrufen eines Ordners anhand des Namens](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Gewusst wie: Programmgesteuertes Erstellen von benutzerdefinierten Ordnerelementen](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  