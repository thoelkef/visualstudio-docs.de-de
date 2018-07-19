---
title: Datenklassenvererbung (O / R-Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6c6b17ad38e9aae78975e43797931a326955712d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756736"
---
# <a name="data-class-inheritance-or-designer"></a>Datenklassenvererbung (O/R Designer)

Wie bei anderen Objekten die LINQ to SQL-Klassen kann Vererbung verwenden und aus anderen Klassen abgeleitet werden. Im Code können Sie Vererbungsbeziehungen zwischen Objekten angeben, indem Sie deklarieren, dass eine Klasse von einer anderen erbt. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Die **Object Relational Designer** (**O/R Designer**) unterstützt das Konzept der Vererbung einer einzelnen Tabelle aus, wie häufig in relationalen Systemen implementierte.

Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Spalten sowohl für Basisklassen als auch für abgeleitete Klassen enthält. Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der festlegt, zu welcher Klasse ein bestimmter Datensatz gehört. Betrachten Sie beispielsweise eine `Persons` Tabelle, die alle in einem Unternehmen enthält. Einige Personen sind Mitarbeiter, andere Führungskräfte. Die `Persons` Tabelle enthält eine Spalte namens `Type` mit dem Wert 1 für Manager und den Wert 2 für Mitarbeiter. Die `Type` Spalte dient als Unterscheidungsspalte. In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und füllen Sie die Klasse nur mit Datensätzen, die eine `Type` Wert 2.

Wenn Sie Konfigurieren der Vererbung in Entitätsklassen unter Verwendung der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], ziehen Sie die einzelne Tabelle, die die von Vererbungsdaten in den Designer, zweimal enthält: einmal für jede Klasse in der Vererbungshierarchie. Nachdem Sie die Tabellen zum Designer hinzufügen, verbinden Sie sie mit einem Vererbungselement aus der **Object Relational Designer** Toolbox, und klicken Sie dann Set die vier Vererbungseigenschaften im der **Eigenschaften** Fenster.

## <a name="inheritance-properties"></a>Vererbungseigenschaften

In der folgenden Tabelle sind die Vererbungseigenschaften mit den jeweiligen Beschreibungen aufgeführt:

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**Unterscheidungseigenschaft**|Die (der Spalte zugeordnete) Eigenschaft, durch die bestimmt wird, zu welcher Klasse der aktuelle Datensatz gehört.|
|**Basis-Diskriminatorwert**|Der Wert (in der Spalte als die **Unterscheidungseigenschaft**), der bestimmt, dass ein Datensatz der Basisklasse ist.|
|**Abgeleiteter Klassendiskriminatorwert**|Der Wert (in der Eigenschaft, die als die **Unterscheidungseigenschaft**), der bestimmt, dass ein Datensatz der abgeleiteten Klasse ist.|
|**Vererbungsstandard**|Die Klasse, die aufgefüllt, wenn der Wert in der Eigenschaft als festgelegt die **Unterscheidungseigenschaft** stimmt nicht überein, entweder die **Basisklassen-Diskriminatorwert** oder **abgeleitete Klasse Diskriminatorwert**.|

Das Erstellen eines Objektmodells, das Vererbung verwendet und sich auf relationale Daten bezieht, kann etwas verwirrend sein. Dieses Thema enthält Informationen über die grundlegenden Begriffe und einzelnen Eigenschaften, die zum Konfigurieren der Vererbung erforderlich sind. Die folgenden Themen enthalten eine genauere Erklärung der Vorgehensweise: Konfigurieren der Vererbung mit dem **O/R Designer**.

|Thema|Beschreibung|
|-----------|-----------------|
|[Gewusst wie: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Beschreibt das Konfigurieren von Entitätsklassen, die Vererbung einer einzelnen Tabelle mithilfe der **O/R Designer**.|
|[Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe der Vererbung einer einzelnen Tabelle (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Enthält schrittweise Anleitungen zum Konfigurieren von Entitätsklassen, die Vererbung einer einzelnen Tabelle mithilfe der **O/R Designer**.|

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe der Vererbung einer einzelnen Tabelle (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Erste Schritte](/dotnet/framework/data/adonet/sql/linq/getting-started)