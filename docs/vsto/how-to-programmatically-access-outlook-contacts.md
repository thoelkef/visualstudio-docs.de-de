---
title: "Gewusst wie: Programmgesteuertes Zugreifen auf Outlook-Kontakte | Microsoft Docs"
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
  - "Kontakte [Office-Entwicklung in Visual Studio], Suchen"
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Gewusst wie: Programmgesteuertes Zugreifen auf Outlook-Kontakte
  In diesem Beispiel werden alle Kontakte gesucht, deren Nachname eine angegebene Suchzeichenfolge enthält.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Beispiel  
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/backup/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/VB/thisaddin.vb#1)]  
  
## Kompilieren des Codes  
 Dieses Beispiel setzt Folgendes voraus:  
  
-   Kontakte im **Kontakteordner**, deren Nachname die Zeichenfolge **"Na"** enthält \(z. B. Tzipi Butnaru\).  
  
## Siehe auch  
 [Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Gewusst wie: Programmgesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Gewusst wie: Programmgesteuerte Suche einer E-Mail-Adresse in den Kontakten](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Gewusst wie: Programmgesteuertes Löschen von Outlook-Kontakten](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  