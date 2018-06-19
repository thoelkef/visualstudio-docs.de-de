---
title: Übersicht über Visual Studio-O/R-Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: acb279780db1291d62cde8202268e0990a56ea64
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924079"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL-tools in Visual Studio

LINQ to SQL ist die erste objektrelationales Mapping-Technologie von Microsoft veröffentlicht wurden. Es funktioniert gut in grundlegende Szenarien und weiterhin in Visual Studio unterstützt werden, aber es ist nicht mehr in der aktiven Entwicklung. Verwenden Sie LINQ to SQL, wenn eine ältere Anwendung zu verwalten, die er bereits verwendet wird, oder in einfachen Anwendungen, die mithilfe von SQL Server und erfordern keine Zuordnung mit mehreren Tabellen. Neue Anwendungen sollten im Allgemeinen das Entity Framework verwenden, wenn eine Ebene objektrelationalen Mapper erforderlich ist.

In Visual Studio erstellen Sie LINQ to SQL-Klassen, die SQL-Tabellen mithilfe der Object Relational Designer (O/R-Designer) darstellen.

Der O/R-Designer hat zwei verschiedene Bereiche auf seiner Entwurfsoberfläche: den Entitätenbereich auf der linken Seite und den Methodenbereich auf der rechten Seite. Der Entitätenbereich ist die Hauptentwurfsoberfläche, auf der Entitätsklassen, Zuordnungen und Vererbungshierarchien angezeigt werden. Der Methodenbereich ist die Entwurfsoberfläche, die zeigt die <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind.

Der O/R-Designer bietet eine visuelle Entwurfsoberfläche zum Erstellen von [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) Entitätsklassen und Zuordnungen (Beziehungen), die auf Objekte in einer Datenbank basieren. Das heißt, dient der O/R-Designer in einer Anwendung ein Objektmodell zu erstellen, die den Objekten in einer Datenbank entspricht. Außerdem generiert er einen stark typisierten <xref:System.Data.Linq.DataContext>, mit dem Daten an die Entitätsklassen gesendet und aus der Datenbank empfangen werden. Der O/R-Designer auch bietet Funktionen zum Zuordnen gespeicherter Prozeduren und Funktionen <xref:System.Data.Linq.DataContext> -Methoden zum Zurückgeben von Daten und Füllen von Entitätsklassen. Schließlich bietet der O/R-Designer die Möglichkeit, vererbungsbeziehungen zwischen Entitätsklassen Entwurf.

## <a name="open-the-or-designer"></a>Öffnen Sie den O/R-designer

Um eine LINQ to SQL-Entität-Objektmodell zum Projekt hinzuzufügen, wählen **Projekt** > **neues Element hinzufügen**, und wählen Sie dann **LINQ to SQL-Klassen** aus der Liste der Projektelemente:

![LINQ to SQL-Klassen](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio erstellt eine DBML-Datei und der Projektmappe hinzugefügt. Dies ist die XML-Zuordnungsdatei und die zugehörigen Code-Dateien.

![LINQ to SQL-Klassen im Projektmappen-Explorer](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Wenn Sie die DBML-Datei auswählen, zeigt Visual Studio die Oberfläche des O/R-Designers, die Ihnen ermöglicht, das Modell visuell zu erstellen. Die folgende Abbildung zeigt den Designer, nachdem die Northwind Customers und Orders-Tabellen aus Server-Explorer gezogen haben. Beachten Sie die Beziehung zwischen den Tabellen.

![LINQ to SQL-Designer](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Der O/R-Designer ist eine einfache objektrelationale Zuordnungen, da er nur 1:1-zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Eine komplexe Zuordnung, z. B. das Zuordnen einer Entitätsklasse zu einer verknüpften Tabelle wird nicht unterstützt. Verwenden Sie das Entity Framework für komplexe Zuordnung. Darüber hinaus ist der Designer ein unidirektionaler Code-Generator. Das bedeutet, dass in der Codedatei nur Änderungen der Designeroberfläche wiedergegeben werden. Manuelle Änderungen der Codedatei werden in den O/R-Designer nicht berücksichtigt. Änderungen, die Sie manuell in der Codedatei werden überschrieben, wenn der Designer gespeichert und Code neu generiert wird. Informationen zum Hinzufügen von Benutzercode und erweitern Sie die Klassen, die vom O/R-Designer generiert, finden Sie unter [wie: Erweitern Code, die von O/R-Designer generiert](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Erstellen Sie und konfigurieren Sie den DataContext hinzu

Nach dem Hinzufügen einer **LINQ to SQL-Klassen** Element zu einem Projekt, und öffnen Sie den O/R-Designer, die leere Entwurfsoberfläche stellt ein leeres <xref:System.Data.Linq.DataContext> bereit für die Konfiguration. die <xref:System.Data.Linq.DataContext> mit Verbindungsinformationen des ersten Elements, das auf die Entwurfsoberfläche gezogen wird konfiguriert... Aus diesem Grund die <xref:System.Data.Linq.DataContext> wird mithilfe der Verbindungsinformationen des ersten Elements auf der Entwurfsoberfläche abgelegt werden konfiguriert. Weitere Informationen zu den <xref:System.Data.Linq.DataContext> Klasse finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Erstellen von Entitätsklassen, die Datenbanktabellen und-Ansichten zugeordnet

Erstellen Sie Entitätsklassen, die durch Ziehen von Datenbanktabellen und-Sichten aus Tabellen und Ansichten zugeordnet **Server-Explorer**/**Datenbank-Explorer** in den O/R-Designer. Wie im vorherigen Abschnitt angegeben die <xref:System.Data.Linq.DataContext> konfiguriert ist, mit der Verbindungsinformationen des ersten Elements, das auf die Entwurfsoberfläche gezogen wird. Wenn ein nachfolgendes Element, das einer anderen Verbindung in den O/R-Designer hinzugefügt wird, können Sie ändern, dass die Verbindung für die <xref:System.Data.Linq.DataContext>. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von LINQ to SQL-Klassen, die mit Tabellen und Sichten (O/R-Designer) zugeordnet](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Erstellen Sie DataContext-Methoden, die gespeicherten Prozeduren und Funktionen aufrufen.

Sie können erstellen <xref:System.Data.Linq.DataContext> Methoden, die aufgerufen werden (zugeordnet werden) gespeicherte Prozeduren und Funktionen von Drag & Drop aus **Server-Explorer**/**Datenbank-Explorer** in den O/R-Designer. Gespeicherte Prozeduren und Funktionen werden als Methoden in den O/R-Designer hinzugefügt der <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Beim Ziehen von gespeicherten Prozeduren und Funktionen aus **Server-Explorer**/**Datenbank-Explorer** in den O/R-Designer, der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methoden unterscheiden sich in Je nachdem, wo Sie das Element ablegen. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurieren von DataContext, um gespeicherte Prozeduren zu verwenden, um Daten zwischen Entitätsklassen und einer Datenbank speichern

Wie bereits angemerkt wurde, können <xref:System.Data.Linq.DataContext>-Methoden erstellt werden, die gespeicherte Prozeduren und Funktionen aufrufen. Darüber hinaus können Sie gespeicherte Prozeduren zuweisen, die für das standardmäßige LINQ to SQL-Laufzeitverhalten verwendet werden können, die Einfüge-, Update- und Löschvorgänge durchführt. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Vererbung und der O/R-designer

Wie andere Objekte die LINQ to SQL-Klassen kann Vererbung verwenden und aus anderen Klassen abgeleitet werden. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Der O/R-Designer unterstützt das Konzept der Vererbung einer einzelnen Tabelle aus, wie häufig in relationalen Systemen implementierte. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren der Vererbung mithilfe des O/R-Designers](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL-Abfragen

Die Entitätsklassen, die vom O/R-Designer erstellt wurden, dienen zur Verwendung mit [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/). Weitere Informationen finden Sie unter [wie: Abfragen von Informationen](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Trennen Sie den generierten DataContext und Entität-Klasse Code in verschiedenen namespaces

Der O/R-Designer bietet die **Context Namespace** und **Entity Namespace** Eigenschaften für die <xref:System.Data.Linq.DataContext>. Mit diesen Eigenschaften wird festgelegt in welchen Namespace der <xref:System.Data.Linq.DataContext> und der Entitätsklassencode generiert werden. Standardmäßig sind diese Eigenschaften leer, und der <xref:System.Data.Linq.DataContext> und die Entitätsklassen werden in den Namespace der Anwendung generiert. Um den Code in einem Namespace als die Anwendung generieren, geben Sie einen Wert in der **Context Namespace** und/oder **Entity Namespace** Eigenschaften.

## <a name="reference-content"></a>Referenzmaterial

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL ((.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Häufig gestellte Fragen ((.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)