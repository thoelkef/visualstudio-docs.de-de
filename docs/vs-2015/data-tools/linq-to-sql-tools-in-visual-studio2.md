---
title: LINQ to SQL Tools | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 470cfabd54fa5f2b92001a635477c60d45fac538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651513"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL-Tools in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL war die erste Objekt relationale Mapping-Technologie, die von Microsoft veröffentlicht wurde. Dies funktioniert in einfachen Szenarien gut und wird in Visual Studio weiterhin unterstützt, ist jedoch nicht mehr in der aktiven Entwicklung. Verwenden Sie LINQ to SQL, wenn Sie eine ältere Anwendung verwalten, die Sie bereits verwendet, oder in einfachen Anwendungen, die SQL Server verwenden und keine Zuordnung mit mehreren Tabellen benötigen. Im Allgemeinen sollten neue Anwendungen die Entity Framework verwenden, wenn eine Objekt relationale Mapper-Ebene erforderlich ist.

 In Visual Studio erstellen Sie LINQ to SQL Klassen, die SQL-Tabellen darstellen, mithilfe von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] verfügt über zwei unterschiedliche Bereiche auf der Entwurfs Oberfläche: der Bereich Entitäten auf der linken Seite und der Bereich Methoden auf der rechten Seite. Der Entitätenbereich ist die Hauptentwurfsoberfläche, auf der Entitätsklassen, Zuordnungen und Vererbungshierarchien angezeigt werden. Der Methodenbereich ist die Entwurfsoberfläche, auf der die <xref:System.Data.Linq.DataContext>-Methoden angezeigt werden, die gespeicherten Prozeduren und Funktionen zugeordnet sind.

 Der [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) stellt eine visuelle Entwurfs Oberfläche zum Erstellen von [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) Entitäts Klassen und-Zuordnungen (Beziehungen) bereit, die auf Objekten in einer Datenbank basieren. Mit anderen Worten: Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird verwendet, um in einer Anwendung ein Objektmodell zu erstellen, das den Objekten in einer Datenbank entspricht. Außerdem generiert er einen stark typisierten <xref:System.Data.Linq.DataContext>, mit dem Daten an die Entitätsklassen gesendet und aus der Datenbank empfangen werden. Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] stellt auch Funktionen bereit, um gespeicherte Prozeduren und Funktionen <xref:System.Data.Linq.DataContext>-Methoden zum Zurückgeben von Daten und Füllen von Entitätsklassen zuzuordnen. Abschließend bietet der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] die Möglichkeit, Vererbungsbeziehungen zwischen Entitätsklassen zu entwerfen.

## <a name="opening-the-or-designer"></a>Öffnen des O/R-Designers
 Um dem Projekt ein LINQ to SQL Entitäts Modell hinzuzufügen, wählen Sie **Projekt &#124; neues Element hinzufügen** aus, und wählen Sie dann  **LINQ to SQL Klassen** aus der Liste der Projekt Elemente aus:

 ![LINQ to SQL-Klassen](../data-tools/media/raddata-linq-to-sql-classes.png "LINQ to SQL Klassen für raddata")

 Visual Studio erstellt eine DBML-Datei und fügt Sie der Projekt Mappe hinzu. Dies ist die XML-Mapping-Datei und die zugehörigen Code Dateien.

 ![LINQ to SQL Klassen in Projektmappen-Explorer](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL-Klassen in Projektmappen-Explorer")

 Wenn Sie die DBML-Datei auswählen, zeigt Visual Studio die O/R-Designer Oberfläche an, die es Ihnen ermöglicht, das Modell visuell zu erstellen. In der folgenden Abbildung ist der Designer dargestellt, nachdem die Northwind-Kunden und Orders-Tabellen aus Server-Explorer gezogen wurden. Beachten Sie die Beziehung zwischen den Tabellen.

 ![LINQ to SQL-Designer](../data-tools/media/raddata-linq-to-sql-designer.png "raddata-LINQ to SQL-Designer")

> [!IMPORTANT]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Ist ein einfaches objektrelationaler Mapper, da er nur 1:1-Zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Eine komplexe Zuordnung, wie z. b. die Zuordnung einer Entitäts Klasse zu einer verbundenen Tabelle, wird nicht unterstützt. Verwenden Sie die Entity Framework für die komplexe Zuordnung. Darüber hinaus ist der Designer ein unidirektionaler Code-Generator. Das bedeutet, dass in der Codedatei nur Änderungen der Designeroberfläche wiedergegeben werden. Manuelle Änderungen der Codedatei werden nicht im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] angezeigt. In der Codedatei vorgenommene manuelle Änderungen werden überschrieben, wenn der Designer gespeichert und Code erneut generiert wird. Weitere Informationen zum Hinzufügen von Benutzercode und Erweitern der vom generierten Klassen finden Sie unter Gewusst [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] [wie: Erweitern von durch den O/R-Designer generierten Code](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Erstellen und Konfigurieren von DataContext
 Nachdem Sie einem Projekt ein **LINQ to SQL Classes** -Element hinzugefügt und das geöffnet [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] haben, stellt die leere Entwurfs Oberfläche einen leeren <xref:System.Data.Linq.DataContext> bereit, der konfiguriert werden kann. die <xref:System.Data.Linq.DataContext> wird mit Verbindungsinformationen konfiguriert, die vom ersten Element bereitgestellt werden, das auf die Entwurfs Oberfläche gezogen wird. Deshalb wird die Klasse <xref:System.Data.Linq.DataContext> mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf der Entwurfsoberfläche abgelegt wird. Weitere Informationen zur- <xref:System.Data.Linq.DataContext> Klasse finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Erstellen von Entitätsklassen, die Datenbanktabellen und -ansichten zugeordnet sind
 Sie können Entitäts Klassen erstellen, die Tabellen und Sichten zugeordnet sind, indem Sie Datenbanktabellen und-Sichten von **Server-Explorer** / **Datenbank-Explorer** auf das ziehen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Wie im vorherigen Abschnitt angegeben <xref:System.Data.Linq.DataContext> , wird die mit Verbindungsinformationen konfiguriert, die vom ersten Element, das auf die Entwurfs Oberfläche gezogen wird, bereitgestellt werden. Wenn ein nachfolgendes Element mit einer anderen Verbindung dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] hinzugefügt wird, können Sie die Verbindung für <xref:System.Data.Linq.DataContext> ändern. Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen von LINQ to SQL Klassen, die Tabellen und Ansichten zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Erstellen von DataContext-Methoden, die gespeicherte Prozeduren und Funktionen aufrufen
 Sie können <xref:System.Data.Linq.DataContext> Methoden erstellen, die gespeicherte Prozeduren und Funktionen aufzurufen, indem Sie Sie von **Server-Explorer** / **Datenbank-Explorer** auf das ziehen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Gespeicherte Prozeduren und Funktionen werden dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] als Methoden vom <xref:System.Data.Linq.DataContext> hinzugefügt.

> [!NOTE]
> Wenn Sie gespeicherte Prozeduren und Funktionen aus **Server-Explorer** / **Datenbank-Explorer** auf das ziehen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , unterscheidet sich der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methode je nachdem, wo Sie das Element ablegen. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurieren von DataContext, um mithilfe von gespeicherten Prozeduren Daten zwischen Entitätsklassen und einer Datenbank zu speichern
 Wie bereits angemerkt wurde, können <xref:System.Data.Linq.DataContext>-Methoden erstellt werden, die gespeicherte Prozeduren und Funktionen aufrufen. Weiterhin können dem standardmäßigen [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Laufzeitverhalten auch gespeicherte Prozeduren zum Durchführen von Einfüge-, Update- und Löschvorgänge zugewiesen werden. Weitere Informationen finden Sie unter Gewusst [wie: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktualisierungen, Einfügungen und Löschungen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Vererbung und der O/R-Designer
 Wie andere Objekte können [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Klassen die Vererbung verwenden und aus anderen Klassen abgeleitet werden. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] unterstützt das häufig in relationalen Systemen implementierte Konzept der Vererbung einer einzelnen Tabelle. Weitere Informationen finden Sie unter Gewusst [wie: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL-Abfragen
 Die von erstellten Entitäts Klassen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sind für die Verwendung mit [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)konzipiert. Weitere Informationen finden Sie unter Vorgehens [Weise: Abfragen von Informationen](https://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Trennen des generierten DataContext und des Entitätsklassencodes in verschiedene Namespaces
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Stellt die Eigenschaften für den **Kontext Namespace** und den **Entitäts Namespace** in bereit <xref:System.Data.Linq.DataContext> . Mit diesen Eigenschaften wird festgelegt in welchen Namespace der <xref:System.Data.Linq.DataContext> und der Entitätsklassencode generiert werden. Standardmäßig sind diese Eigenschaften leer, und der <xref:System.Data.Linq.DataContext> und die Entitätsklassen werden in den Namespace der Anwendung generiert. Geben Sie einen Wert in die Eigenschaften **Context Namespace** und/oder **Entity Namespace** ein, um den Code in einem anderen Namespace als dem der Anwendung zu generieren.

## <a name="in-this-section"></a>In diesem Abschnitt
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md) Erläutert <xref:System.Data.Linq.DataContext> , welche Methoden und wie Sie erstellt werden.

 [Daten Klassen Vererbung (O/R-Designer)](../data-tools/data-class-inheritance-o-r-designer.md) Beschreibt das Konzept der Vererbung einer einzelnen Tabelle und deren Implementierung in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 Vorgehens [Weise: Erstellen von LINQ to SQL Klassen, die Tabellen und Ansichten zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) Beschreibt das Erstellen von Entitäts Klassen, die Tabellen und Sichten in einer-Datenbank zugeordnet sind.

 Gewusst [wie: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL Klassen (O/R-Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) Beschreibt das Erstellen einer Beziehung zwischen [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Entitäts Klassen.

 Gewusst [wie: Erstellen von DataContext-Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) Beschreibt das Erstellen von <xref:System.Data.Linq.DataContext> Methoden, die gespeicherte Prozeduren oder Funktionen ausführen, wenn Sie aufgerufen werden.

 Vorgehens [Weise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Aktualisierungen, Einfügungen und Löschungen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) Beschreibt, wie eine so konfiguriert wird <xref:System.Data.Linq.DataContext> , dass gespeicherte Prozeduren verwendet werden, wenn Daten aus Entitäts Klassen in einer Datenbank wieder gespeichert werden

 [Vorgehensweise: Ändern des Rückgabe Typs einer DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) Beschreibt, wie der Rückgabetyp einer <xref:System.Data.Linq.DataContext> Methode auf den Typ einer Entitäts Klasse oder auf einen automatisch generierten Typ festgelegt wird, der vom O/R-Designer erstellt wurde.

 Gewusst [wie: Hinzufügen von Validierungen zu Entitäts Klassen](../data-tools/how-to-add-validation-to-entity-classes.md) Beschreibt, wie partielle Methoden generiert werden, die das Hinzufügen von Code bei Eigenschafts Änderungen und Entitäts Klassen Aktualisierungen ermöglichen.

 Gewusst [wie: Aktivieren und Deaktivieren der Pluralisierung (O/R-Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) Beschreibt, wie das automatische Umbenennen von Klassen, die der hinzugefügt werden, aktiviert und deaktiviert wird [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 Vorgehens [Weise: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Beschreibt das Konfigurieren von Entitäts Klassen mithilfe einer Vererbung einer einzelnen Tabelle mit dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 Gewusst [wie: Erweitern von durch den O/R-Designer generierten Code](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) Beschreibt, wie und wo Sie Code hinzufügen können, der nicht überschrieben wird, wenn Änderungen an Objekten im O/R-Designer Code neu generieren.

 Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen mithilfe einer Vererbung für eine einzelne Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) Enthält Schritt-für-Schritt-Anleitungen zum Konfigurieren von Entitäts Klassen mithilfe einer Vererbung einer einzelnen Tabelle mit dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 Exemplarische Vorgehensweise [: Anpassen des Einfüge-, Aktualisierungs-und Lösch Verhaltens von Entitäts Klassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) Enthält Schritt-für-Schritt-Anweisungen zum Konfigurieren von für <xref:System.Data.Linq.DataContext> die Verwendung gespeicherter Prozeduren beim zurück speichern von Daten aus Entitäts Klassen in einer Datenbank.

## <a name="reference-content"></a>Referenz Inhalt
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Weitere Informationen
 [Häufig gestellte Fragen](https://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [zu Visual Studio Data Tools für .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
