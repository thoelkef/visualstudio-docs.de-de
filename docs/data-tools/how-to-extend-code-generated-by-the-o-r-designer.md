---
title: "Vorgehensweise: Erweitern von mit dem O/R-Designer generiertem Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vorgehensweise: Erweitern von mit dem O/R-Designer generiertem Code
Code, der vom [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] generiert wurde, wird erneut generiert, wenn Änderungen an der Entitätsklasse und an anderen Objekten auf der Designeroberfläche vorgenommen werden.Aufgrund dieser erneuten Codegenerierung wird in der Regel jeglicher Code, der zum generierten Code hinzugefügt wurde, überschrieben, sobald vom Designer neuer Code generiert wird.Der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] bietet die Möglichkeit, Dateien mit partiellen Klassen zu generieren, denen Code hinzugefügt werden kann, der nicht überschrieben wird.Ein Beispiel für das Hinzufügen eigenen Codes zu dem von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] generierten Code, ist das Hinzufügen der Datenvalidierung zu LINQ to SQL\-\(Entitäts\)\-Klassen.Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Hinzufügen von Code zu einer Entitätsklasse  
  
#### So erstellen Sie eine partielle Klasse und fügen Code zu einer Entitätsklasse hinzu  
  
1.  Erstellen Sie eine neue LINQ to SQL\-Klassendatei \(**.dbml**\-Datei\) im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], oder öffnen Sie eine vorhandene Datei.\(Doppelklicken Sie im **Projektmappen\-Explorer**\/**Datenbank\-Explorer** auf die **DBML**\-Datei.\)  
  
2.  Klicken Sie im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] mit der rechten Maustaste auf die Klasse, der Sie Validierungen hinzufügen möchten, und klicken Sie dann auf **Code anzeigen**.  
  
     Der Code\-Editor wird mit einer partiellen Klasse für die ausgewählte Entitätsklasse geöffnet.  
  
3.  Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für die Entitätsklasse hinzu.  
  
## Hinzufügen von Code zu einem DataContext  
  
#### So erstellen Sie eine partielle Klasse und fügen Code zu einem DataContext hinzu  
  
1.  Erstellen Sie eine neue LINQ to SQL\-Klassendatei \(**.dbml**\-Datei\) im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], oder öffnen Sie eine vorhandene Datei.\(Doppelklicken Sie im **Projektmappen\-Explorer**\/**Datenbank\-Explorer** auf die **DBML**\-Datei.\)  
  
2.  Klicken Sie im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] mit der rechten Maustaste auf einen leeren Bereich des Designers, und klicken Sie dann auf **Code anzeigen**.  
  
     Der Code\-Editor wird mit einer partiellen Klasse für den DataContext geöffnet.  
  
3.  Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für den DataContext hinzu.  
  
## Siehe auch  
 [Übersicht über den O\/R\-Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Exemplarische Vorgehensweise: Hinzufügen von Validierung zu Entitätsklassen](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md)