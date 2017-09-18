---
title: "Vorgehensweise: Konfigurieren von Vererbung mit dem O/R-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 4
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vorgehensweise: Konfigurieren von Vererbung mit dem O/R-Designer
Der [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) unterstützt das häufig in relationalen Systemen implementierte Konzept der Vererbung einer einzelnen Tabelle. Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Felder sowohl für übergeordnete Informationen als auch für untergeordnete Informationen enthält.Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der festlegt, zu welcher Klasse ein bestimmter Datensatz gehört.  
  
 Betrachten Sie beispielsweise die Tabelle "Persons", die alle in einem Unternehmen beschäftigten Personen enthält.Einige Personen sind Mitarbeiter, andere Führungskräfte.Die Tabelle "Persons" enthält die Spalte `EmployeeType`, die für Führungskräfte den Wert 1 und für Mitarbeiter den Wert 2 enthält. Diese Spalte dient als Unterscheidungsspalte.In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und die Klasse nur mit Datensätzen füllen, die einen `EmployeeType`\-Wert von 2 aufweisen.Sie können aus der jeweiligen Klasse auch die nicht zutreffenden Spalten entfernen.  
  
 Das Erstellen eines Objektmodells, das Vererbung verwendet \(und sich auf relationale Daten bezieht\), kann etwas verwirrend sein.Im folgenden Verfahren werden die erforderlichen Schritte zum Konfigurieren von Vererbung mit dem O\/R\-Designer dargestellt.Da es möglicherweise schwierig ist, generische Schritte nachzuvollziehen, ohne sich auf eine vorhandene Tabelle und die zugehörigen Spalten zu beziehen, wird auch eine exemplarische Vorgehensweise zur Verfügung gestellt, in der echte Daten verwendet werden.Ausführliche Schritt\-für\-Schritt\-Anleitungen zur Konfiguration von Vererbung mit dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] finden Sie unter [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen mithilfe von Vererbung einer einzelnen Tabelle \(O\/R\-Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
### So erstellen Sie geerbte Datenklassen  
  
1.  Öffnen Sie den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], indem Sie einem vorhandenen Visual Basic\- oder C\#\-Projekt ein **LINQ to SQL\-Klassen**\-Element hinzufügen.  
  
2.  Ziehen Sie die Tabelle, die Sie als Basisklasse verwenden möchten, auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Ziehen Sie eine zweite Kopie der Tabelle auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], und benennen Sie sie um.Sie dient als abgeleitete Klasse bzw. Unterklasse.  
  
4.  Klicken Sie in der **Toolbox** auf der Registerkarte **O\/R\-Designer** auf **Vererbung**, klicken Sie dann auf die Unterklasse \(die umbenannte Tabelle\), und stellen Sie eine Verbindung mit der Basisklasse her.  
  
    > [!NOTE]
    >  Klicken Sie in der **Toolbox** auf das Element **Vererbung**, und lassen Sie die Maustaste los. Klicken Sie auf die zweite Kopie der in Schritt 3 erstellten Klasse, und klicken Sie dann auf die erste Klasse, die Sie in Schritt 2 erstellt haben.Der Pfeil der Vererbungslinie zeigt dann auf die erste Klasse.  
  
5.  Löschen Sie in jeder Klasse die Objekteigenschaften, die nicht angezeigt werden sollen und die nicht für Zuordnungen verwendet werden.Der Versuch, für Zuordnungen verwendete Objekteigenschaften zu löschen, führt zu einem Fehler: [Die \<Eigenschaftenname\>\-Eigenschaft kann nicht gelöscht werden, weil sie an der Zuordnung \<Zuordnungsname\> teilnimmt](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Da eine abgeleitete Klasse die in der Basisklasse definierten Eigenschaften erbt, dürfen in den Klassen nicht dieselben Spalten definiert sein.\(Spalten werden als Eigenschaften implementiert.\) Sie können die Erstellung von Spalten in der abgeleiteten Klasse ermöglichen, indem Sie in der Basisklasse den Vererbungsmodifizierer für die entsprechende Eigenschaft festlegen.Weitere Informationen finden Sie unter [NOT IN BUILD: Overriding Properties and Methods](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
6.  Wählen Sie im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] die Vererbungslinie aus.  
  
7.  Legen Sie im Fenster **Eigenschaften** die **Unterscheidungseigenschaft** auf den Namen der Spalte fest, anhand der die Datensätze in den Klassen unterschieden werden.  
  
8.  Legen Sie die Eigenschaft **Abgeleiteter Klassendiskriminatorwert** auf den Wert in der Datenbank fest, der den Datensatz als den geerbten Typ kennzeichnet.\(Dies ist der Wert, der in der Unterscheidungsspalte gespeichert und mit dem die geerbte Klasse gekennzeichnet wird.\)  
  
9. Legen Sie die Eigenschaft **Basisklassen\-Diskriminatorwert** auf den Wert fest, der den Datensatz als Basistyp kennzeichnet.\(Dies ist der eigentliche Wert, der in der Unterscheidungsspalte gespeichert und mit dem die Basisklasse gekennzeichnet wird.\)  
  
10. Wahlweise können Sie auch die Eigenschaft **Vererbungsstandard** festlegen, um in einer Vererbungshierarchie einen Typ zu kennzeichnen, der beim Laden von Spalten verwendet wird, die keinem definierten Vererbungscode entsprechen.Mit anderen Worten: Wenn ein Datensatz in der Unterscheidungsspalte einen Wert enthält, der keinem der Werte in den Eigenschaften **Abgeleiteter Klassendiskriminatorwert** oder **Basisklassen\-Diskriminatorwert** entspricht, wird der Datensatz in den als **Vererbungsstandard** gekennzeichneten Typ geladen.  
  
## Siehe auch  
 [Übersicht über den O\/R\-Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/de-de/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen mithilfe von Vererbung einer einzelnen Tabelle \(O\/R\-Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/de-de/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Vererbung](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)