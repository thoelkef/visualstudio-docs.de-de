---
title: 'Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 2a68101b6090a20526088309a441956a68e875e9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014665"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer
Die **Object Relational Designer** (**O/R Designer**) unterstützt das Konzept der Vererbung einer einzelnen Tabelle aus, wie häufig in relationalen Systemen implementierte. Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Felder sowohl für übergeordnete Informationen als auch für untergeordnete Informationen enthält. Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der festlegt, zu welcher Klasse ein bestimmter Datensatz gehört.

Betrachten Sie beispielsweise eine `Persons` Tabelle, die alle in einem Unternehmen enthält. Einige Personen sind Mitarbeiter, andere Führungskräfte. Die `Persons` Tabelle enthält eine Spalte namens `EmployeeType` mit dem Wert 1 für Manager und den Wert 2 für Mitarbeiter; Dies dient als Unterscheidungsspalte. In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und die Klasse nur mit Datensätzen füllen, die einen `EmployeeType`-Wert von 2 aufweisen. Sie können aus der jeweiligen Klasse auch die nicht zutreffenden Spalten entfernen.

Das Erstellen eines Objektmodells, das Vererbung verwendet (und sich auf relationale Daten bezieht), kann etwas verwirrend sein. Im folgenden Verfahren werden die erforderlichen Schritte zum Konfigurieren von Vererbung mit dem **O/R-Designer** dargestellt. Generischen Schritte ohne Verweis auf eine vorhandene Tabelle und Spalten kann schwierig sein, damit eine exemplarische Vorgehensweise mit Daten bereitgestellt wird. Weitere schrittweise Anleitungen zum Konfigurieren der Vererbung mithilfe der **O/R Designer**, finden Sie unter [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mit einer Vererbung für eine einzelne Tabelle (O/R-Designer)

## <a name="to-create-inherited-data-classes"></a>So erstellen Sie geerbte Datenklassen

1.  Öffnen der **O/R Designer** durch Hinzufügen einer **LINQ to SQL-Klassen** Element zu einem vorhandenen Visual Basic oder C# Projekt.

2.  Ziehen Sie die Tabelle, die Sie als Basisklasse in verwenden möchten die **O/R Designer**.

3.  Ziehen Sie eine zweite Kopie der Tabelle auf die **O/R Designer** und benennen Sie sie. Sie dient als abgeleitete Klasse bzw. Unterklasse.

4.  Klicken Sie in der **Toolbox** auf der Registerkarte **Objektrelationaler Designer** auf **Vererbung**, klicken Sie dann auf die Unterklasse (die umbenannte Tabelle), und stellen Sie eine Verbindung mit der Basisklasse her.

    > [!NOTE]
    >  Klicken Sie in der **Toolbox** auf das Element **Vererbung**, und lassen Sie die Maustaste los. Klicken Sie auf die zweite Kopie der in Schritt 3 erstellten Klasse, und klicken Sie dann auf die erste Klasse, die Sie in Schritt 2 erstellt haben. Der Pfeil der Vererbungslinie zeigt auf die erste Klasse.

5.  Löschen Sie in jeder Klasse die Objekteigenschaften, die nicht angezeigt werden sollen und die nicht für Zuordnungen verwendet werden. Erhalten Sie eine Fehlermeldung, wenn Sie versuchen, die für Zuordnungen verwendete Objekteigenschaften zu löschen: [Die Eigenschaft \<Eigenschaftenname> kann nicht gelöscht werden, weil sie Teil der Zuordnung \<Zuordnungsname> ist](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md)

    > [!NOTE]
    >  Da eine abgeleitete Klasse die in der Basisklasse definierten Eigenschaften erbt, dürfen in den Klassen nicht dieselben Spalten definiert sein. (Spalten werden als Eigenschaften implementiert.) Sie können die Erstellung von Spalten in der abgeleiteten Klasse ermöglichen, indem Sie in der Basisklasse den Vererbungsmodifizierer für die entsprechende Eigenschaft festlegen. Weitere Informationen finden Sie unter [Grundlagen der Vererbung (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6.  Wählen Sie die von-Vererbungszeile in der **O/R Designer**.

7.  In der **Eigenschaften** legen die **Unterscheidungseigenschaft** auf den Namen der Spalte, mit dem die Datensätze in den Klassen unterschieden.

8.  Legen Sie die Eigenschaft **Abgeleiteter Klassendiskriminatorwert** auf den Wert in der Datenbank fest, der den Datensatz als den geerbten Typ kennzeichnet. (Dies ist der Wert, der in der Unterscheidungsspalte gespeichert und wird verwendet, um die geerbte Klasse gekennzeichnet.)

9. Legen Sie die Eigenschaft **Basisklassen-Diskriminatorwert** auf den Wert fest, der den Datensatz als Basistyp kennzeichnet. (Dies ist der Wert, der in der Unterscheidungsspalte gespeichert und wird verwendet, um die Basisklasse gekennzeichnet.)

10. Wahlweise können Sie auch die Eigenschaft **Vererbungsstandard** festlegen, um in einer Vererbungshierarchie einen Typ zu kennzeichnen, der beim Laden von Spalten verwendet wird, die keinem definierten Vererbungscode entsprechen. Das heißt, wenn ein Datensatz einen Wert in der Unterscheidungsspalte enthält, die entspricht nicht der Werte in der **abgeleiteter Klassendiskriminatorwert** oder **Basisklassen-Diskriminatorwert** Eigenschaften, die den Datensatz in den Typ als lädt die **Vererbungsstandard**.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mit einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Grundlagen der Vererbung (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Vererbung](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)