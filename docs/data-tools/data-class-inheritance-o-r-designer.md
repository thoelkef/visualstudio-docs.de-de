---
title: "Vererbung von Datenklassen (O/R-Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vererbung von Datenklassen (O/R-Designer)
Wie andere Objekte können [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]\-Klassen die Vererbung verwenden und aus anderen Klassen abgeleitet werden.Im Code können Sie Vererbungsbeziehungen zwischen Objekten angeben, indem Sie deklarieren, dass eine Klasse von einer anderen erbt.Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt.Der [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) unterstützt das häufig in relationalen Systemen implementierte Konzept der Vererbung einer einzelnen Tabelle.  
  
 Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Spalten sowohl für Basisklassen als auch für abgeleitete Klassen enthält.Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der festlegt, zu welcher Klasse ein bestimmter Datensatz gehört.Betrachten Sie beispielsweise die Tabelle Persons, die alle in einem Unternehmen beschäftigten Personen enthält.Einige Personen sind Mitarbeiter, andere Führungskräfte.Die Tabelle Persons enthält die Spalte Type, die für Führungskräfte den Wert 1 und für Mitarbeiter den Wert 2 enthält.Der Spalte Type dient als Unterscheidungsspalte.In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und die Klasse nur mit Datensätzen füllen, die den Type\-Wert 2 haben.  
  
 Wenn Sie die Vererbung in Entitätsklassen unter Verwendung von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] konfigurieren, ziehen Sie die einzelne Tabelle, die die Vererbungsdaten enthält, zweimal auf den Designer: einmal für jede Klasse in der Vererbungshierarchie.Nachdem Sie dem Designer die Tabellen hinzugefügt haben, verbinden Sie sie mit einem Vererbungselement aus der **Object Relational Designer**\-Toolbox und legen dann die vier Vererbungseigenschaften im **Eigenschaftenfenster** fest.  
  
## Vererbungseigenschaften  
 In der folgenden Tabelle sind die Vererbungseigenschaften mit den jeweiligen Beschreibungen aufgeführt:  
  
|Eigenschaft|Beschreibung|  
|-----------------|------------------|  
|Unterscheidungseigenschaft|Die \(der Spalte zugeordnete\) Eigenschaft, durch die bestimmt wird, zu welcher Klasse der aktuelle Datensatz gehört.|  
|Basisklassen\-Diskriminatorwert|Der Wert \(in der durch die Unterscheidungseigenschaft angegebenen Spalte\), durch den bestimmt wird, das ein Datensatz der Basisklasse angehört.|  
|Diskriminatorwert der abgeleiteten Klasse|Der Wert \(in der als Unterscheidungseigenschaft bezeichneten Eigenschaft\), durch den bestimmt wird, dass ein Datensatz der abgeleiteten Klasse angehört.|  
|Vererbungsstandard|Die Klasse, die mit Daten gefüllt werden soll, wenn der Wert in der als **Unterscheidungseigenschaft** bezeichneten Eigenschaft weder dem **Basisklassen\-Diskriminatorwert** noch dem **Diskriminatorwert der abgeleiteten Klasse** entspricht.|  
  
 Das Erstellen eines Objektmodells, das Vererbung verwendet und sich auf relationale Daten bezieht, kann etwas verwirrend sein.Dieses Thema enthält Informationen über die grundlegenden Begriffe und einzelnen Eigenschaften, die zum Konfigurieren der Vererbung erforderlich sind.Die folgenden Themen enthalten eine genauere Erklärung darüber, wie die Vererbung mit dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] konfiguriert wird.  
  
|Thema|Beschreibung|  
|-----------|------------------|  
|[Vorgehensweise: Konfigurieren von Vererbung mit dem O\/R\-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Beschreibt das Konfigurieren von Entitätsklassen, die Vererbung für eine einzelne Tabelle verwenden, mit dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|  
|[Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen mithilfe von Vererbung einer einzelnen Tabelle \(O\/R\-Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Bietet schrittweise Anweisungen zum Konfigurieren von Entitätsklassen, die Vererbung für eine einzelne Tabelle verwenden, mithilfe von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|  
  
## Siehe auch  
 [Übersicht über den O\/R\-Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen \(O\/R\-Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL\-Klassen mithilfe von Vererbung einer einzelnen Tabelle \(O\/R\-Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [Erste Schritte](../Topic/Getting%20Started.md)