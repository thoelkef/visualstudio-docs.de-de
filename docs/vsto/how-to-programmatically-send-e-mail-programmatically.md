---
title: "Gewusst wie: Programmgesteuertes Senden von E-Mails | Microsoft Docs"
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
  - "E-Mail [Office-Entwicklung in Visual Studio], Senden"
  - "E-Mail-Elemente [Office-Entwicklung in Visual Studio], Senden von E-Mail"
  - "Outlook [Office-Entwicklung in Visual Studio], Erstellen von E-Mail"
  - "Outlook [Office-Entwicklung in Visual Studio], Senden von E-Mail"
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Programmgesteuertes Senden von E-Mails
  In diesem Beispiel wird eine E\-Mail\-Nachricht an alle Kontakte versendet, deren E\-Mail\-Adresse den Domänennamen **example.com** enthält.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Beispiel  
 [!code-csharp[Trin_OL_ProgramEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_ProgramEMail/CS/thisaddin.cs#1)]  
  
## Kompilieren des Codes  
 Dieses Beispiel setzt Folgendes voraus:  
  
-   Kontakte, deren E\-Mail\-Adresse den Domänennamen **example.com** enthält.  
  
## Robuste Programmierung  
 Entfernen Sie keinesfalls den Filtercode, der nach dem Domänennamen **example.com** sucht.  Ohne den Filter wird die E\-Mail\-Nachricht an alle Kontakte gesendet.  
  
## Siehe auch  
 [Arbeiten mit E-Mail-Elementen](../vsto/working-with-mail-items.md)   
 [Gewusst wie: Programmgesteuertes Erstellen von E-Mail-Elementen](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Gewusst wie: Programmgesteuertes Zugreifen auf Outlook-Kontakte](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Gewusst wie: Programmgesteuertes Ausführen von Aktionen beim Empfang einer E-Mail-Nachricht](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  