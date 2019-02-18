---
title: Übersicht über den O/R-Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4105a93d4ad459c8bc1cb3a7a20b37c69f311c12
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931636"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL-Tools in Visual Studio

LINQ to SQL war die erste objektrelationales Mapping-Technologie von Microsoft veröffentlicht. Es funktioniert gut in grundlegenden Szenarien und weiterhin in Visual Studio unterstützt werden, aber es ist nicht mehr in der aktiven Entwicklung. Verwenden Sie LINQ to SQL, wenn eine ältere Anwendung verwaltet, die es bereits verwendet wird, oder in einfache Anwendungen, die SQL Server verwenden und erfordern keine mit mehreren Tabellen zuordnen. Neue Anwendungen sollten im Allgemeinen das Entity Framework verwenden, wenn eine objektrelationale Zuordnung-Ebene erforderlich ist.

In Visual Studio, erstellen Sie LINQ to SQL-Klassen, die darstellen, SQL-Tabellen mithilfe der **Object Relational Designer** (**O/R Designer**).

Die **O/R Designer** verfügt über zwei verschiedene Bereiche auf seiner Entwurfsoberfläche: den Entitätenbereich auf der linken Seite und den Methodenbereich auf der rechten Seite. Der Entitätenbereich ist die Hauptentwurfsoberfläche, auf der Entitätsklassen, Zuordnungen und Vererbungshierarchien angezeigt werden. Der Methodenbereich ist die Entwurfsoberfläche, auf der die <xref:System.Data.Linq.DataContext>-Methoden angezeigt werden, die gespeicherten Prozeduren und Funktionen zugeordnet sind.

Die **O/R Designer** bietet eine visuelle Entwurfsoberfläche zum Erstellen von [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) -Entitätsklassen und-Zuordnungen (Beziehungen), die auf Objekte in einer Datenbank basieren. Das heißt, die **O/R Designer** erstellt ein Objekt in einer Anwendung, die Objekte in einer Datenbank zugeordnet ist. Außerdem generiert er einen stark typisierten <xref:System.Data.Linq.DataContext> , sendet und empfängt Daten zwischen Entitätsklassen und der Datenbank. Die **O/R Designer** auch bietet Funktionen zum Zuordnen gespeicherter Prozeduren und Funktionen <xref:System.Data.Linq.DataContext> Methoden zum Zurückgeben von Daten und Füllen von Entitätsklassen. Zum Schluss die **O/R Designer** bietet die Möglichkeit zum Entwerfen von vererbungsbeziehungen zwischen Entitätsklassen.

## <a name="open-the-or-designer"></a>Öffnen Sie den O/R-designer

Wählen Sie zum Hinzufügen einer LINQ to SQL-Entity-Datenmodell zu Ihrem Projekt **Projekt** > **neues Element hinzufügen**, und wählen Sie dann **LINQ to SQL-Klassen** aus der Liste der Projektelemente:

![LINQ to SQL-Klassen](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio erstellt eine *dbml* Datei und fügt es der Projektmappe hinzu. Dies ist die XML-Zuordnungsdatei und die zugehörigen Code-Dateien.

![LINQ to SQL-Klassen im Projektmappen-Explorer](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Bei der Auswahl der *dbml* -Datei, zeigt Visual Studio die **O/R Designer** Oberfläche, die Ihnen zur visuellen Erstellung des Modells ermöglicht. Die folgende Abbildung zeigt den Designer nach der Northwind `Customers` und `Orders` Tabellen verfügen über gezogen wurden **Server-Explorer**. Beachten Sie die Beziehung zwischen den Tabellen.

![LINQ to SQL-Designer](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Die **O/R Designer** ist eine einfache objektrelationale Zuordnungen, da es nur 1:1-zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Komplexe Zuordnungen, z. B. die Zuordnung einer Entitätsklasse zu einer verknüpften Tabelle, wird nicht unterstützt. Verwenden Sie das Entity Framework für die komplexe Zuordnung. Darüber hinaus ist der Designer ein unidirektionaler Code-Generator. Das bedeutet, dass in der Codedatei nur Änderungen der Designeroberfläche wiedergegeben werden. Manuelle Änderungen an der Codedatei werden nicht wiedergegeben, der **O/R Designer**. In der Codedatei vorgenommene manuelle Änderungen werden überschrieben, wenn der Designer gespeichert und Code erneut generiert wird. Informationen zum Hinzufügen von Benutzercode und erweitern die Klassen, die vom der **O/R-Designer**, finden Sie unter [wie: Erweitern von O/R-Designer generierten Code](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Erstellen Sie und konfigurieren Sie den DataContext

Nach dem Hinzufügen einer **LINQ to SQL-Klassen** Element zu einem Projekt, und Öffnen der **O/R Designer**, die leere Entwurfsoberfläche stellt ein leeres <xref:System.Data.Linq.DataContext> bereit für die Konfiguration. Die Klasse <xref:System.Data.Linq.DataContext> wird mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf die Entwurfsoberfläche gezogen wird. Deshalb wird die Klasse <xref:System.Data.Linq.DataContext> mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf der Entwurfsoberfläche abgelegt wird. Weitere Informationen zu den <xref:System.Data.Linq.DataContext> Klasse finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Erstellen von Entitätsklassen, die Datenbanktabellen und-Sichten zugeordnet

Sie können Entitätsklassen, die zu Tabellen und Ansichten zugeordnet sind, durch Ziehen von Datenbanktabellen und-Sichten aus erstellen **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R Designer**. Wie im vorherigen Abschnitt angegeben, wird die Klasse <xref:System.Data.Linq.DataContext> mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf die Entwurfsoberfläche gezogen wird. Wenn ein nachfolgendes Element, das einer anderen Verbindung hinzugefügt wird die **O/R Designer**, Sie können ändern, dass die Verbindung für die <xref:System.Data.Linq.DataContext>. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von LINQ to SQL-Klassen zu Tabellen und Sichten (O/R Designer) zugeordnet](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Erstellen Sie DataContext-Methoden, die gespeicherten Prozeduren und Funktionen aufrufen.

Sie erstellen <xref:System.Data.Linq.DataContext> Methoden, die aufgerufen werden (zugeordnet) gespeicherte Prozeduren und Funktionen durch Ziehen von **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R-Designer** . Gespeicherte Prozeduren und Funktionen hinzugefügt werden die **O/R Designer** Methoden wie die <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Beim Ziehen von gespeicherten Prozeduren und Funktionen von **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R Designer**, der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methode hängt davon ab, in dem Sie das Element ablegen. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurieren von DataContext, um gespeicherte Prozeduren zu verwenden, um Daten zwischen Entitätsklassen und einer Datenbank speichern

Wie bereits angemerkt wurde, können <xref:System.Data.Linq.DataContext>-Methoden erstellt werden, die gespeicherte Prozeduren und Funktionen aufrufen. Darüber hinaus können Sie auch gespeicherte Prozeduren zuweisen, die für die Standardinstanz verwendet werden, LINQ to SQL-Laufzeitverhalten, die ausführt, einfügungen, Updates, und löscht. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Vererbung und der O/R-Designer

Wie bei anderen Objekten die LINQ to SQL-Klassen kann Vererbung verwenden und aus anderen Klassen abgeleitet werden. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Die **O/R Designer** unterstützt das Konzept der Vererbung einer einzelnen Tabelle aus, wie häufig in relationalen Systemen implementierte. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL-Abfragen

Die Entitätsklassen erstellt die **O/R Designer** dienen zur Verwendung mit [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/). Weitere Informationen finden Sie unter [Vorgehensweise: Abfragen von Informationen](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Trennen Sie den generierten DataContext und Entity-Klasse-Code in verschiedene namespaces

Die **O/R Designer** bietet die **Kontext Namespace** und **Entity Namespace** Eigenschaften für die <xref:System.Data.Linq.DataContext>. Mit diesen Eigenschaften wird festgelegt in welchen Namespace der <xref:System.Data.Linq.DataContext> und der Entitätsklassencode generiert werden. Standardmäßig sind diese Eigenschaften leer, und der <xref:System.Data.Linq.DataContext> und die Entitätsklassen werden in den Namespace der Anwendung generiert. Geben Sie einen Wert in die Eigenschaften **Context Namespace** und/oder **Entity Namespace** ein, um den Code in einem anderen Namespace als dem der Anwendung zu generieren.

## <a name="reference-content"></a>Verweisen auf Inhalte

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Häufig gestellte Fragen ((.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)