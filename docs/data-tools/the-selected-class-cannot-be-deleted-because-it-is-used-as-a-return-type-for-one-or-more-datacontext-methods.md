---
title: "Die ausgew&#228;hlte Klasse kann nicht gel&#246;scht werden, da sie als R&#252;ckgabetyp f&#252;r mindestens eine DataContext-Methode verwendet wird | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Die ausgew&#228;hlte Klasse kann nicht gel&#246;scht werden, da sie als R&#252;ckgabetyp f&#252;r mindestens eine DataContext-Methode verwendet wird
Der Rückgabetyp mindestens einer <xref:System.Data.Linq.DataContext>\-Methode ist die ausgewählte Entitätsklasse.Durch das Löschen einer Entitätsklasse, die als Rückgabetyp für eine <xref:System.Data.Linq.DataContext>\-Methode verwendet wird, tritt bei der Kompilierung des Projekts ein Fehler auf.Zum Löschen der ausgewählten Entitätsklasse identifizieren Sie die <xref:System.Data.Linq.DataContext>\-Methoden, die sie verwenden, und legen Sie deren Rückgabetypen auf eine andere Entitätsklasse fest.  
  
 Für das Zurücksetzen der Rückgabetypen von <xref:System.Data.Linq.DataContext>\-Methoden auf ihre ursprünglichen, automatisch erstellten Typen löschen Sie zunächst die <xref:System.Data.Linq.DataContext>\-Methode aus dem Methodenbereich und ziehen anschließend das Objekt aus dem **Server\-Explorer**\/**Datenbank\-Explorer** erneut in den O\/R\-Designer.  
  
### So beheben Sie diesen Fehler  
  
1.  Identifizieren Sie die <xref:System.Data.Linq.DataContext>\-Methoden, die diese Entitätsklasse als Rückgabetyp verwenden, indem Sie im Methodenbereich eine <xref:System.Data.Linq.DataContext>\-Methode auswählen und im Fenster **Eigenschaften** die Eigenschaft **Rückgabetyp** überprüfen.  
  
2.  Legen Sie den **Rückgabewert** auf eine andere Entitätsklasse fest, oder entfernen Sie die <xref:System.Data.Linq.DataContext>\-Methode aus dem Methodenbereich.  
  
## Siehe auch  
 [Übersicht über den O\/R\-Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Ändern des Rückgabetyps einer DataContext\-Methode \(O\/R\-Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)