---
title: Datenklassenvererbung (O/R-Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: f0e95466baa4e16e4620ff387a11d4e723399a38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953392"
---
# <a name="data-class-inheritance-or-designer"></a>Datenklassenvererbung (O/R-Designer)

Wie bei anderen Objekten die LINQ to SQL-Klassen kann Vererbung verwenden und aus anderen Klassen abgeleitet werden. Im Code können Sie Vererbungsbeziehungen zwischen Objekten angeben, indem Sie deklarieren, dass eine Klasse von einer anderen erbt. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Die **Object Relational Designer** (**O/R Designer**) unterstützt das Konzept der Vererbung einer einzelnen Tabelle aus, wie häufig in relationalen Systemen implementierte.

Bei der Vererbung einer einzelnen Tabelle gibt es eine einzelne Datenbanktabelle, die Spalten sowohl für Basisklassen als auch für abgeleitete Klassen enthält. Bei relationalen Daten enthält eine Unterscheidungsspalte den Wert, der festlegt, zu welcher Klasse ein bestimmter Datensatz gehört. Betrachten Sie beispielsweise eine `Persons` Tabelle, die alle in einem Unternehmen enthält. Einige Personen sind Mitarbeiter, andere Führungskräfte. Die `Persons` Tabelle enthält eine Spalte namens `Type` mit dem Wert 1 für Manager und den Wert 2 für Mitarbeiter. Die `Type` Spalte dient als Unterscheidungsspalte. In diesem Szenario können Sie eine Unterklasse von Mitarbeitern erstellen und füllen Sie die Klasse nur mit Datensätzen, die eine `Type` Wert 2.

Wenn Sie die Vererbung in Entitätsklassen unter Verwendung von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] konfigurieren, ziehen Sie die einzelne Tabelle, die die Vererbungsdaten enthält, zweimal auf den Designer: einmal für jede Klasse in der Vererbungshierarchie. Nachdem Sie dem Designer die Tabellen hinzugefügt haben, verbinden Sie sie mit einem Vererbungselement aus der Toolbox des **objektrelationaler Designers** und legen dann die vier Vererbungseigenschaften im Fenster **Eigenschaften** fest.

## <a name="inheritance-properties"></a>Vererbungseigenschaften

In der folgenden Tabelle sind die Vererbungseigenschaften mit den jeweiligen Beschreibungen aufgeführt:

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**Diskriminatoreigenschaft**|Die (der Spalte zugeordnete) Eigenschaft, durch die bestimmt wird, zu welcher Klasse der aktuelle Datensatz gehört.|
|**Basisklassen-Diskriminatorwert**|Der Wert (in der durch die **Diskriminatoreigenschaft** angegebenen Spalte), durch den bestimmt wird, das ein Datensatz der Basisklasse angehört.|
|**Diskriminatorwert der abgeleiteten Klasse**|Der Wert (in der als **Diskriminatoreigenschaft** bezeichneten Eigenschaft), durch den bestimmt wird, dass ein Datensatz der abgeleiteten Klasse angehört.|
|**Vererbungsstandard**|Die Klasse, die aufgefüllt, wenn der Wert in der Eigenschaft als festgelegt die **Unterscheidungseigenschaft** stimmt nicht überein, entweder die **Basisklassen-Diskriminatorwert** oder **abgeleitete Klasse Diskriminatorwert**.|

Das Erstellen eines Objektmodells, das Vererbung verwendet und sich auf relationale Daten bezieht, kann etwas verwirrend sein. Dieses Thema enthält Informationen über die grundlegenden Begriffe und einzelnen Eigenschaften, die zum Konfigurieren der Vererbung erforderlich sind. Die folgenden Themen enthalten eine genauere Erklärung der Vorgehensweise: Konfigurieren der Vererbung mit dem **O/R Designer**.

|Thema|Beschreibung|
|-----------|-----------------|
|[Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Beschreibt das Konfigurieren von Entitätsklassen, die Vererbung einer einzelnen Tabelle mithilfe der **O/R Designer**.|
|[Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mit einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Enthält schrittweise Anleitungen zum Konfigurieren von Entitätsklassen, die Vererbung einer einzelnen Tabelle mithilfe der **O/R Designer**.|

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mit einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Erste Schritte](/dotnet/framework/data/adonet/sql/linq/getting-started)