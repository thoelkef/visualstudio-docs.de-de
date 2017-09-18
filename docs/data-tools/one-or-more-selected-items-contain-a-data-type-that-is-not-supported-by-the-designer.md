---
title: "Mindestens ein ausgew&#228;hltes Element enth&#228;lt einen Datentyp, der vom Designer nicht unterst&#252;tzt wird | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 4
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mindestens ein ausgew&#228;hltes Element enth&#228;lt einen Datentyp, der vom Designer nicht unterst&#252;tzt wird
Mindestens eines der aus dem **Server\-Explorer**\/**Datenbank\-Explorer** auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] gezogenen Elemente enthält einen Datentyp, der vom [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] nicht unterstützt wird \(z. B. [Benutzerdefinierte CLR\-Typen](../Topic/CLR%20User-Defined%20Types.md)\).  
  
### So beheben Sie diesen Fehler  
  
1.  Erstellen Sie eine auf der gewünschten Tabelle basierende Sicht, in der der nicht unterstützte Datentyp nicht enthalten ist.  
  
2.  Ziehen Sie die Sicht aus dem **Server\-Explorer**\/**Datenbank\-Explorer** auf den Designer.  
  
## Siehe auch  
 [Übersicht über den O\/R\-Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)