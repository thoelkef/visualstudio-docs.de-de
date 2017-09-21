---
title: "DataContext-Methoden (O/R-Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 5
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DataContext-Methoden (O/R-Designer)
<xref:System.Data.Linq.DataContext>\-Methoden sind \(im Kontext von [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)\) Methoden der <xref:System.Data.Linq.DataContext>\-Klasse, die gespeicherte Prozeduren und Funktionen in einer Datenbank ausführen.  
  
 Die <xref:System.Data.Linq.DataContext>\-Klasse ist eine [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Klasse, die als Verbindung zwischen einer SQL Server\-Datenbank und den [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Entitätsklassen dient, die dieser Datenbank zugeordnet sind.Die <xref:System.Data.Linq.DataContext>\-Klasse enthält die Verbindungszeichenfolgeninformationen und die Methoden zum Herstellen einer Verbindung mit einer Datenbank und zum Ändern der Daten in der Datenbank. Standardmäßig enthält die <xref:System.Data.Linq.DataContext>\-Klasse mehrere Methoden, die Sie aufrufen können, z. B. die <xref:System.Data.Linq.DataContext.SubmitChanges%2A>\-Methode, die aktualisierte Daten aus [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Klassen an die Datenbank sendet.Sie können auch zusätzliche <xref:System.Data.Linq.DataContext>\-Methoden erstellen, die gespeicherten Prozeduren und Funktionen zugeordnet werden.Mit anderen Worten: Durch das Aufrufen dieser benutzerdefinierten Methoden wird in der Datenbank die gespeicherte Prozedur oder die Funktion ausgeführt, der die <xref:System.Data.Linq.DataContext>\-Methode zugeordnet ist.Sie können der <xref:System.Data.Linq.DataContext>\-Klasse neue Methoden hinzufügen, wie Sie auch anderen Klassen Methoden hinzufügen würden, um diese zu erweitern.Bei den Erläuterungen von <xref:System.Data.Linq.DataContext>\-Methoden im Kontext von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] werden jedoch die <xref:System.Data.Linq.DataContext>\-Methoden besprochen, die gespeicherten Prozeduren und Funktionen zugeordnet werden.  
  
> [!NOTE]
>  In [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] werden gespeicherte Prozeduren und Funktionen auf dieselbe Weise behandelt: sowohl gespeicherte Prozeduren als auch Funktionen werden Entitätsklassen mit demselben <xref:System.Data.Linq.StoredProcedureAttribute> zugeordnet.Im Kontext von [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] entsprechen die <xref:System.Data.Linq.DataContext>\-Methoden, die gespeicherten Prozeduren zugeordnet sind, denen, die Funktionen zugeordnet sind.  
  
## Methodenbereich  
 Die gespeicherten Prozeduren und Funktionen zugeordneten <xref:System.Data.Linq.DataContext>\-Methoden werden im Methodenbereich von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] angezeigt.Der Methodenbereich befindet sich neben dem Bereich **Entitäten** \(der Hauptentwurfsoberfläche\).Im Methodenbereich werden alle <xref:System.Data.Linq.DataContext>\-Methoden aufgelistet, die Sie mit dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] erstellt haben.Standardmäßig ist der Methodenbereich leer. Ziehen Sie gespeicherte Prozeduren oder Funktionen aus dem **Server\-Explorer**\/**Datenbank\-Explorer** auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], um <xref:System.Data.Linq.DataContext>\-Methoden zu erstellen und den Methodenbereich zu füllen.Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von DataContext\-Methoden, die gespeicherten Prozeduren und Funktionen \(O\/R\-Designer\) zugeordnet sind](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Sie können den Methodenbereich öffnen bzw. schließen, indem Sie mit der rechten Maustaste auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] und dann auf **Methodenbereich ausblenden** bzw. **Methodenbereich anzeigen** klicken oder die Tastenkombination STRG\+1 verwenden.  
  
## Zwei Typen von DataContext\-Methoden  
 DataContext\-Methoden sind Methoden, die gespeicherten Prozeduren und Funktionen in der Datenbank zugeordnet werden.DataContext\-Methoden können im Methodenbereich des [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] erstellt und hinzugefügt werden.Es gibt zwei verschiedene Typen von <xref:System.Data.Linq.DataContext>\-Methoden, die sich dadurch unterscheiden, dass von dem einen ein oder mehrere Resultsets zurückgegeben werden und von dem anderen nicht:  
  
-   <xref:System.Data.Linq.DataContext>\-Methoden, die ein oder mehrere Resultsets zurückgeben:  
  
     Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext>\-Methode, wenn eine Anwendung nur gespeicherte Prozeduren und Funktionen in der Datenbank ausführen und die Ergebnisse zurückgeben muss.Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von DataContext\-Methoden, die gespeicherten Prozeduren und Funktionen \(O\/R\-Designer\) zugeordnet sind](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), <xref:System.Data.Linq.ISingleResult%271> und <xref:System.Data.Linq.IMultipleResults>.  
  
-   <xref:System.Data.Linq.DataContext>\-Methoden, die keine Resultsets zurückgeben, wie Einfüge\-, Update\- und Löschvorgänge für eine bestimmte Entitätsklasse.  
  
     Erstellen Sie diese Art von <xref:System.Data.Linq.DataContext>\-Methode, wenn eine Anwendung gespeicherte Prozeduren ausführen muss, statt das [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Standardverhalten zum Speichern geänderter Daten zwischen einer Entitätsklasse und der Datenbank zu verwenden.Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchführung von Update\-, Einfüge\- und Löschvorgängen \(O\/R\-Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Rückgabetypen von DataContext\-Methoden  
 Wenn Sie gespeicherte Prozeduren und Funktionen aus dem **Server\-Explorer**\/**Datenbank\-Explorer** auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ziehen, unterscheidet sich der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext>\-Methode je nach dem Ort, an dem Sie das Element ablegen.Durch Ablegen des Elements direkt auf einer vorhandenen Entitätsklasse wird eine <xref:System.Data.Linq.DataContext>\-Methode mit dem Rückgabetyp der Entitätsklasse erstellt. Durch Ablegen von Elementen in einem \(beliebigen\) leeren [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\-Bereich wird eine <xref:System.Data.Linq.DataContext>\-Methode erstellt, die einen automatisch generierten Typ zurückgibt.Der automatisch generierte Typ erhält einen Namen, der dem der gespeicherten Prozedur oder Funktion entspricht, und Eigenschaften, die den von der gespeicherten Prozedur oder Funktion zurückgegebenen Feldern entsprechen.  
  
> [!NOTE]
>  Sie können den Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode ändern, nachdem Sie sie dem Methodenbereich hinzugefügt haben.Um den Rückgabetyp einer <xref:System.Data.Linq.DataContext>\-Methode zu überprüfen oder zu ändern, markieren Sie sie, und überprüfen Sie die Eigenschaft **Rückgabetyp** im Fenster **Eigenschaften**.Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Rückgabetyps einer DataContext\-Methode \(O\/R\-Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Objekte, die von der Datenbank auf die Oberfläche des O\/R\-Designers gezogen werden, werden nach den Namen der Objekte in der Datenbank automatisch benannt.Wenn dasselbe Objekt mehrfach auf die Oberfläche gezogen wird, wird an das Ende des neuen Namens eine Nummer angehängt, damit die Namen unterschieden werden können.Wenn Namen von Datenbankobjekten Leerzeichen oder in Visual Basic oder C\# nicht unterstützte Zeichen enthalten, wird das entsprechende Zeichen durch einen Unterstrich ersetzt.  
  
## Siehe auch  
 [Object Relational Designer \(O\/R\-Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Gespeicherte Prozeduren](../Topic/Stored%20Procedures.md)   
 [Vorgehensweise: Erstellen von DataContext\-Methoden, die gespeicherten Prozeduren und Funktionen \(O\/R\-Designer\) zugeordnet sind](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zur Durchführung von Update\-, Einfüge\- und Löschvorgängen \(O\/R\-Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Exemplarische Vorgehensweise: Anpassen des Einfüge\-, Update\- und Löschverhaltens von Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)