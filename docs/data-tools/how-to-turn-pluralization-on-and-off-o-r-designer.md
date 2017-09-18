---
title: "Vorgehensweise: An- und Ausschalten der Pluralisierung (O/R-Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vorgehensweise: An- und Ausschalten der Pluralisierung (O/R-Designer)
Werden Datenbankobjekte, deren Namen auf s oder ies enden, aus dem **Server\-Explorer**\/**Datenbank\-Explorer** in den [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) gezogen, so werden die Namen der erzeugten Entitätsklassen standardmäßig von der Plural\- in die Singularform geändert.Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist.Wird dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] beispielsweise die Tabelle Customers hinzugefügt, erhält die Entitätsklasse den Namen Customer, da die Klasse die Daten eines einzigen Kunden enthält.  
  
> [!NOTE]
>  Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### So schalten Sie Pluralisierung ein und aus  
  
1.  Klicken Sie im Menü **Extras**  auf **Optionen**.  
  
2.  Erweitern Sie im Dialogfeld **Optionen** den Knoten **Datenbanktools**.  
  
> [!NOTE]
>  Wählen Sie **Alle Einstellungen anzeigen** aus, wenn der Knoten **Datenbanktools** nicht angezeigt wird.  
  
1.  Klicken Sie auf **O\/R\-Designer**.  
  
2.  Legen Sie **Pluralisierung von Namen** auf **Aktiviert** \= **False** fest, um den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] so einzustellen, dass Klassennamen nicht geändert werden.  
  
3.  Legen Sie **Pluralisierung von Namen** auf **Aktiviert** \= **True** fest, damit Pluralisierungsregeln auf die Klassennamen von Objekten angewendet werden, die dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] hinzugefügt werden.  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)