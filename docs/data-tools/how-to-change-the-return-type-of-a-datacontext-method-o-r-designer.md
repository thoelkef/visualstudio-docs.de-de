---
title: "Vorgehensweise: &#196;ndern des R&#252;ckgabetyps einer DataContext-Methode (O/R-Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vorgehensweise: &#196;ndern des R&#252;ckgabetyps einer DataContext-Methode (O/R-Designer)
Der Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode, die basierend auf einer gespeicherten Prozedur oder Funktion erstellt wurde, unterscheidet sich abhängig von dem Ort, an dem die gespeicherte Prozedur oder Funktion im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] abgelegt wurde.Wenn Sie ein Element direkt auf einer vorhandene Entitätsklasse ablegen, wird eine <xref:System.Data.Linq.DataContext>\-Methode erstellt, die über den Rückgabetyp dieser Entitätsklasse verfügt \(wenn das Schema der Daten, die von der gespeicherten Prozedur oder Funktion zurückgegeben wurden, mit der Form der Entitätsklasse übereinstimmt\).Wenn Sie ein Element in einem leeren Bereich von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ablegen, wird eine <xref:System.Data.Linq.DataContext>\-Methode erstellt, die einen automatisch erstellten Typ zurückgibt.Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode ändern, wenn Sie sie dem Methodenbereich hinzugefügt haben.Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode zu überprüfen oder zu ändern, markieren Sie sie und klicken im Fenster **Eigenschaften** auf die Eigenschaft **Rückgabetyp**.  
  
> [!NOTE]
>  <xref:System.Data.Linq.DataContext>\-Methoden können nicht wiederhergestellt werden, wenn ein Rückgabetyp auf eine Entitätsklasse festgelegt ist, um so den automatisch generierten Typ mithilfe des Fensters **Eigenschaften** zurückzugeben.Zum Wiederherstellen einer <xref:System.Data.Linq.DataContext>\-Methode zur Rückgabe eines automatisch generierten Typs müssen Sie das ursprüngliche Datenbankobjekt erneut auf den O\/R\-Designer ziehen.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### So ändern Sie den Rückgabetyp einer DataContext\-Methode vom automatisch generierten Typ in eine Entitätsklasse  
  
1.  Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>\-Methode aus.  
  
2.  Wählen Sie im Fenster **Eigenschaften** die Option **Rückgabetyp** und anschließend in der Liste **Rückgabetyp** eine verfügbare Entitätsklasse aus.Wenn sich die gewünschte Entitätsklasse nicht in der Liste befindet, fügen Sie sie hinzu oder erstellen sie im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], um sie anschließend der Liste hinzuzufügen.  
  
3.  Speichern Sie die DBML\-Datei.  
  
### So ändern Sie den Rückgabetyp einer DataContext\-Methode von einer Entitätsklasse zurück in einen automatisch generierten Typ  
  
1.  Wählen Sie im Methodenbereich die <xref:System.Data.Linq.DataContext>\-Methode aus, und löschen Sie sie.  
  
2.  Ziehen Sie das Datenbankobjekt von **Server\-Explorer**\/**Datenbank\-Explorer** auf einen leeren Bereich des O\/R\-Designers.  
  
3.  Speichern Sie die DBML\-Datei.  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext\-Methoden \(O\/R\-Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Vorgehensweise: Erstellen von DataContext\-Methoden, die gespeicherten Prozeduren und Funktionen \(O\/R\-Designer\) zugeordnet sind](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)