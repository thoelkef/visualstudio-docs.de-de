---
title: Übersicht über LINQ to SQL O/R-Designer
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 55f6fa2ad9eda2d701563d1fa99c76f5cd5c7c1d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282006"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL-Tools in Visual Studio

LINQ to SQL war die erste Objekt relationale Mapping-Technologie, die von Microsoft veröffentlicht wurde. Dies funktioniert in einfachen Szenarien gut und wird in Visual Studio weiterhin unterstützt, ist jedoch nicht mehr in der aktiven Entwicklung. Verwenden Sie LINQ to SQL, wenn Sie eine ältere Anwendung verwalten, die Sie bereits verwendet, oder in einfachen Anwendungen, die SQL Server verwenden und keine Zuordnung mit mehreren Tabellen benötigen. Im Allgemeinen sollten neue Anwendungen die Entity Framework verwenden, wenn eine Objekt relationale Mapper-Ebene erforderlich ist.

## <a name="install-the-linq-to-sql-tools"></a>Installieren der LINQ to SQL Tools

In Visual Studio erstellen Sie LINQ to SQL Klassen, die SQL-Tabellen darstellen, mithilfe der **objektrelationaler Designer** (**O/R-Designer**). Der O/R-Designer ist die Benutzeroberfläche zum Bearbeiten von DBML-Dateien. Zum Bearbeiten von DBML-Dateien mit einer Designer Oberfläche sind die LINQ to SQL Tools erforderlich, die nicht standardmäßig als Teil der Workloads von Visual Studio installiert werden.

Wenn Sie die LINQ to SQL Tools installieren möchten, starten Sie den Visual Studio-Installer, wählen Sie **ändern**aus, wählen Sie dann die Registerkarte **einzelne Komponenten** aus, und wählen Sie dann **LINQ to SQL Tools** unter der Kategorie **Code Tools** aus.

## <a name="what-is-the-or-designer"></a>Was ist der O/R-Designer?

Der **O/R-Designer** hat zwei unterschiedliche Bereiche auf der Entwurfs Oberfläche: der Bereich Entitäten auf der linken Seite und der Bereich Methoden auf der rechten Seite. Der Entitätenbereich ist die Hauptentwurfsoberfläche, auf der Entitätsklassen, Zuordnungen und Vererbungshierarchien angezeigt werden. Der Methodenbereich ist die Entwurfsoberfläche, auf der die <xref:System.Data.Linq.DataContext>-Methoden angezeigt werden, die gespeicherten Prozeduren und Funktionen zugeordnet sind.

Der **O/R-Designer** stellt eine visuelle Entwurfs Oberfläche zum Erstellen von [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) Entitäts Klassen und-Zuordnungen (Beziehungen) bereit, die auf Objekten in einer Datenbank basieren. Mit anderen Worten: der **O/R-Designer** erstellt in einer Anwendung, die Objekten in einer Datenbank zugeordnet wird, ein Objektmodell. Außerdem wird ein stark typisiertes generiert <xref:System.Data.Linq.DataContext> , das Daten zwischen den Entitäts Klassen und der Datenbank sendet und empfängt. Der **O/R-Designer** bietet auch Funktionen zum Zuordnen gespeicherter Prozeduren und Funktionen zu <xref:System.Data.Linq.DataContext> Methoden zum Zurückgeben von Daten und Auffüllen von Entitäts Klassen. Schließlich bietet der **O/R-Designer** die Möglichkeit, Vererbungs Beziehungen zwischen Entitäts Klassen zu entwerfen.

## <a name="open-the-or-designer"></a>Öffnen Sie den O/R-Designer.

Um dem Projekt ein LINQ to SQL Entitäts Modell hinzuzufügen, wählen Sie **Projekt**  >  **Neues Element hinzufügen**aus, und wählen Sie dann **LINQ to SQL Klassen** aus der Liste der Projekt Elemente aus:

![LINQ to SQL-Klassen](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio erstellt eine *DBML* -Datei und fügt Sie der Projekt Mappe hinzu. Dies ist die XML-Mapping-Datei und die zugehörigen Code Dateien.

![LINQ to SQL Klassen in Projektmappen-Explorer](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Wenn Sie die *DBML* -Datei auswählen, zeigt Visual Studio die **O/R-Designer** Oberfläche an, die es Ihnen ermöglicht, das Modell visuell zu erstellen. Die folgende Abbildung zeigt den Designer, nachdem die Northwind `Customers` -und- `Orders` Tabellen aus **Server-Explorer**gezogen wurden. Beachten Sie die Beziehung zwischen den Tabellen.

![LINQ to SQL-Designer](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Der **O/R-Designer** ist ein einfacher objektrelationaler Mapper, da er nur 1:1-Zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Eine komplexe Zuordnung, wie z. b. die Zuordnung einer Entitäts Klasse zu einer verbundenen Tabelle, wird nicht unterstützt. Verwenden Sie die Entity Framework für die komplexe Zuordnung. Darüber hinaus ist der Designer ein unidirektionaler Code-Generator. Das bedeutet, dass in der Codedatei nur Änderungen der Designeroberfläche wiedergegeben werden. Manuelle Änderungen an der Codedatei werden im **O/R-Designer**nicht widergespiegelt. In der Codedatei vorgenommene manuelle Änderungen werden überschrieben, wenn der Designer gespeichert und Code erneut generiert wird. Weitere Informationen zum Hinzufügen von Benutzercode und Erweitern der vom **o/r-Designer**generierten Klassen finden Sie unter Gewusst [wie: Erweitern von durch den o/r-Designer generierten Code](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Erstellen und Konfigurieren des DataContext

Nachdem Sie einem Projekt ein **LINQ to SQL Classes** -Element hinzugefügt und den **O/R-Designer**geöffnet haben, stellt die leere Entwurfs Oberfläche eine leere <xref:System.Data.Linq.DataContext> bereit, die konfiguriert werden kann. Die Klasse <xref:System.Data.Linq.DataContext> wird mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf die Entwurfsoberfläche gezogen wird. Deshalb wird die Klasse <xref:System.Data.Linq.DataContext> mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf der Entwurfsoberfläche abgelegt wird. Weitere Informationen zur- <xref:System.Data.Linq.DataContext> Klasse finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Erstellen von Entitäts Klassen, die Datenbanktabellen und-Sichten zugeordnet sind

Sie können Entitäts Klassen erstellen, die Tabellen und Sichten zugeordnet sind, indem Sie Datenbanktabellen und-Sichten von **Server-Explorer** oder **Datenbank-Explorer** auf den **O/R-Designer**ziehen. Wie im vorherigen Abschnitt angegeben, wird die Klasse <xref:System.Data.Linq.DataContext> mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf die Entwurfsoberfläche gezogen wird. Wenn ein nachfolgendes Element, das eine andere Verbindung verwendet, dem **O/R-Designer**hinzugefügt wird, können Sie die Verbindung für den ändern <xref:System.Data.Linq.DataContext> . Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen von LINQ to SQL Klassen, die Tabellen und Ansichten zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Erstellen von DataContext-Methoden, die gespeicherte Prozeduren und Funktionen abrufen

Sie können <xref:System.Data.Linq.DataContext> Methoden erstellen, die gespeicherte Prozeduren und Funktionen aufzurufen, indem Sie Sie von **Server-Explorer** oder **Datenbank-Explorer** auf den **O/R-Designer**ziehen. Gespeicherte Prozeduren und Funktionen werden dem **O/R-Designer** als Methoden des hinzugefügt <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> Wenn Sie gespeicherte Prozeduren und Funktionen von **Server-Explorer** oder **Datenbank-Explorer** auf den **O/R-Designer**ziehen, unterscheidet sich der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methode je nachdem, wo Sie das Element ablegen. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurieren eines DataContext für die Verwendung gespeicherter Prozeduren zum Speichern von Daten zwischen Entitäts Klassen und einer Datenbank

Wie bereits angemerkt wurde, können <xref:System.Data.Linq.DataContext>-Methoden erstellt werden, die gespeicherte Prozeduren und Funktionen aufrufen. Außerdem können Sie gespeicherte Prozeduren zuweisen, die für das standardmäßige LINQ to SQL Laufzeitverhalten verwendet werden, das Einfügungen, Aktualisierungen und Löschungen ausführt. Weitere Informationen finden Sie unter Gewusst [wie: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktualisierungen, Einfügungen und Löschungen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Vererbung und der O/R-Designer

Wie bei anderen-Objekten können LINQ to SQL-Klassen die Vererbung verwenden und von anderen Klassen abgeleitet werden. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Der **O/R-Designer** unterstützt das Konzept der Vererbung einer einzelnen Tabelle, da es häufig in relationalen Systemen implementiert wird. Weitere Informationen finden Sie unter Gewusst [wie: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL-Abfragen

Die vom **O/R-Designer** erstellten Entitäts Klassen sind für die Verwendung mit [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)konzipiert. Weitere Informationen finden Sie unter Vorgehens [Weise: Abfragen von Informationen](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Den generierten DataContext-und Entitäts Klassen Code in verschiedene Namespaces aufteilen

Der **O/R-Designer** stellt die **Kontext Namespace** -und **Entitäts Namespace** -Eigenschaften für bereit <xref:System.Data.Linq.DataContext> . Mit diesen Eigenschaften wird festgelegt in welchen Namespace der <xref:System.Data.Linq.DataContext> und der Entitätsklassencode generiert werden. Standardmäßig sind diese Eigenschaften leer, und der <xref:System.Data.Linq.DataContext> und die Entitätsklassen werden in den Namespace der Anwendung generiert. Geben Sie einen Wert in die Eigenschaften **Context Namespace** und/oder **Entity Namespace** ein, um den Code in einem anderen Namespace als dem der Anwendung zu generieren.

## <a name="reference-content"></a>Referenz Inhalt

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Häufig gestellte Fragen (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
