---
title: 'Vorgehensweise: Konfigurieren der Vererbung mithilfe des O-R-Designers | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b53dec270481ca8aa6009b9ddd27bdcdfeae6037
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer
Der [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) unterstützt das häufig in relationalen Systemen implementierte Konzept der Vererbung einer einzelnen Tabelle. Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Felder sowohl für übergeordnete Informationen als auch für untergeordnete Informationen enthält. Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der bestimmt, welche Klasse Datensatz gehört.  
  
Betrachten Sie beispielsweise die Tabelle "Persons", die alle in einem Unternehmen beschäftigten Personen enthält. Einige Personen sind Mitarbeiter, andere Führungskräfte. Die Tabelle "Persons" enthält die Spalte `EmployeeType`, die für Führungskräfte den Wert 1 und für Mitarbeiter den Wert 2 enthält. Diese Spalte dient als Unterscheidungsspalte. In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und die Klasse nur mit Datensätzen füllen, die einen `EmployeeType`-Wert von 2 aufweisen. Sie können aus der jeweiligen Klasse auch die nicht zutreffenden Spalten entfernen.  
  
Das Erstellen eines Objektmodells, das Vererbung verwendet (und sich auf relationale Daten bezieht), kann etwas verwirrend sein. Im folgenden Verfahren werden die erforderlichen Schritte zum Konfigurieren von Vererbung mit dem O/R-Designer dargestellt. Da es möglicherweise schwierig ist, generische Schritte nachzuvollziehen, ohne sich auf eine vorhandene Tabelle und die zugehörigen Spalten zu beziehen, wird auch eine exemplarische Vorgehensweise zur Verfügung gestellt, in der echte Daten verwendet werden. Ausführliche schrittweise Anleitungen zum Konfigurieren der Vererbung mithilfe der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], finden Sie unter [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen, indem Sie mithilfe von Vererbung einer einzelnen Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
## <a name="to-create-inherited-data-classes"></a>So erstellen Sie geerbte Datenklassen
  
1.  Öffnen der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] durch Hinzufügen einer **LINQ to SQL-Klassen** Element zu einem vorhandenen Visual Basic- oder C#-Projekt.  
  
2.  Ziehen Sie die Tabelle, die Sie als Basisklasse verwenden möchten, auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
3.  Ziehen Sie eine zweite Kopie der Tabelle auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] und benennen Sie sie. Sie dient als abgeleitete Klasse bzw. Unterklasse.  
  
4.  Klicken Sie auf **Vererbung** in der **Object Relational Designer** auf der Registerkarte die **Toolbox**, und klicken Sie auf die Unterklasse (die umbenannte Tabelle), und verbinden Sie ihn mit der Basisklasse.  
  
    > [!NOTE]
    >  Klicken Sie auf die **Vererbung** Element in der **Toolbox** und Loslassen der Maustaste, klicken Sie auf die zweite Kopie der in Schritt 3 erstellten Klasse, und klicken Sie dann auf die erste Klasse, die Sie in Schritt 2 erstellt haben. Der Pfeil der Vererbungslinie zeigt dann auf die erste Klasse.  
  
5.  Löschen Sie in jeder Klasse die Objekteigenschaften, die nicht angezeigt werden sollen und die nicht für Zuordnungen verwendet werden. Sie erhalten einen Fehler auf, wenn Sie versuchen, das Löschen von Objekteigenschaften für Zuordnungen verwendet: [Eigenschaft \<Eigenschaftsname > kann nicht gelöscht werden, da sie in der Zuordnung teilnimmt \<Association-Name >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Da eine abgeleitete Klasse die in der Basisklasse definierten Eigenschaften erbt, dürfen in den Klassen nicht dieselben Spalten definiert sein. (Spalten werden als Eigenschaften implementiert.) Sie können die Erstellung von Spalten in der abgeleiteten Klasse ermöglichen, indem Sie in der Basisklasse den Vererbungsmodifizierer für die entsprechende Eigenschaft festlegen. Weitere Informationen finden Sie unter [Grundlagen der Vererbung (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).  
  
6.  Wählen Sie im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] die Vererbungslinie aus.  
  
7.  In der **Eigenschaften** legen die **Unterscheidungseigenschaft** an den Spaltennamen, der verwendet wird, um die Datensätze in Ihren Klassen zu unterscheiden.  
  
8.  Legen Sie die **Diskriminatorwert der abgeleiteten Klasse** -Eigenschaft auf den Wert in der Datenbank, die den Datensatz als den geerbten Typ kennzeichnet. (Dies ist der Wert, der in der Unterscheidungsspalte gespeichert und mit dem die geerbte Klasse gekennzeichnet wird.)  
  
9. Legen Sie die **Basisklassen-Diskriminatorwert** -Eigenschaft auf den Wert, der den Datensatz als Basistyp kennzeichnet. (Dies ist der eigentliche Wert, der in der Unterscheidungsspalte gespeichert und mit dem die Basisklasse gekennzeichnet wird.)  
  
10. Optional können Sie auch Festlegen der **Vererbungsstandard** -Eigenschaft auf einen Typ in einer Vererbungshierarchie zu bestimmen, die beim Laden von Zeilen, die keine entsprechen Vererbungscode definierten verwendet wird. Das heißt, wenn ein Datensatz in der Unterscheidungsspalte einen Wert enthält, der nicht mit der Werte in der **Diskriminatorwert der abgeleiteten Klasse** oder **Basisklassen-Diskriminatorwert** Eigenschaften, die den Datensatz in den Typ als lädt die **Vererbungsstandard**.  
  
## <a name="see-also"></a>Siehe auch
[LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O-R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
[Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe der Vererbung einer einzelnen Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
[Grundlagen der Vererbung (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)  
[Vererbung](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)