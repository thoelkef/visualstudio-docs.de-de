---
title: LINQ to SQL-Tools | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 44e12e616e453dcdc0390e8a6eb5b2065a51a6bb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656933"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL-Tools in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL war die erste objektrelationales Mapping-Technologie von Microsoft veröffentlicht. Es funktioniert gut in grundlegenden Szenarien und weiterhin in Visual Studio unterstützt werden, aber es ist nicht mehr in der aktiven Entwicklung. Verwenden Sie LINQ to SQL, wenn eine ältere Anwendung verwaltet, die es bereits verwendet wird, oder in einfache Anwendungen, die SQL Server verwenden und erfordern keine mit mehreren Tabellen zuordnen. Neue Anwendungen sollten im Allgemeinen das Entity Framework verwenden, wenn eine objektrelationale Zuordnung-Ebene erforderlich ist.

 In Visual Studio, erstellen Sie LINQ to SQL-Klassen, die darstellen, SQL-Tabellen mithilfe der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 Die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] verfügt über zwei verschiedene Bereiche auf seiner Entwurfsoberfläche: den Entitätenbereich auf der linken Seite und den Methodenbereich auf der rechten Seite. Der Entitätenbereich ist die Hauptentwurfsoberfläche, auf der Entitätsklassen, Zuordnungen und Vererbungshierarchien angezeigt werden. Der Methodenbereich ist die Entwurfsoberfläche, auf der die <xref:System.Data.Linq.DataContext>-Methoden angezeigt werden, die gespeicherten Prozeduren und Funktionen zugeordnet sind.

 Die [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) bietet eine visuelle Entwurfsoberfläche zum Erstellen von [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) -Entitätsklassen und-Zuordnungen (Beziehungen), die auf Objekte in einer Datenbank basieren. Mit anderen Worten: Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] wird verwendet, um in einer Anwendung ein Objektmodell zu erstellen, das den Objekten in einer Datenbank entspricht. Außerdem generiert er einen stark typisierten <xref:System.Data.Linq.DataContext>, mit dem Daten an die Entitätsklassen gesendet und aus der Datenbank empfangen werden. Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] stellt auch Funktionen bereit, um gespeicherte Prozeduren und Funktionen <xref:System.Data.Linq.DataContext>-Methoden zum Zurückgeben von Daten und Füllen von Entitätsklassen zuzuordnen. Abschließend bietet der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] die Möglichkeit, Vererbungsbeziehungen zwischen Entitätsklassen zu entwerfen.

## <a name="opening-the-or-designer"></a>Öffnen des O/R-Designers
 Wählen Sie zum Hinzufügen einer LINQ to SQL-Entity-Datenmodell zu Ihrem Projekt **Projekt &#124; neues Element hinzufügen** und wählen Sie dann **LINQ to SQL-Klassen** aus der Liste der Projektelemente:

 ![LINQ to SQL-Klassen](../data-tools/media/raddata-linq-to-sql-classes.png "Raddata LINQ to SQL-Klassen")

 Visual Studio erstellt eine DBML-Datei und fügt es der Projektmappe hinzu. Dies ist die XML-Zuordnungsdatei und die zugehörigen Code-Dateien.

 ![LINQ to SQL-Klassen im Projektmappen-Explorer](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "Raddata LINQ to SQL-Klassen im Projektmappen-Explorer")

 Wenn Sie die DBML-Datei auswählen, zeigt Visual Studio die Oberfläche des O/R-Designers, die Ihnen zur visuellen Erstellung des Modells ermöglicht. Die folgende Abbildung zeigt der Designer nach die Northwind Customers und Orders-Tabellen im Server-Explorer gezogen wurde, haben. Beachten Sie die Beziehung zwischen den Tabellen.

 ![LINQ to SQL-Designer](../data-tools/media/raddata-linq-to-sql-designer.png "Raddata LINQ to SQL-Designer")

> [!IMPORTANT]
>  Die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ist eine einfache objektrelationale Zuordnungen, da es nur 1:1-zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Komplexe Zuordnungen, z. B. die Zuordnung einer Entitätsklasse zu einer verknüpften Tabelle, wird nicht unterstützt. Verwenden Sie das Entity Framework für die komplexe Zuordnung. Darüber hinaus ist der Designer ein unidirektionaler Code-Generator. Das bedeutet, dass in der Codedatei nur Änderungen der Designeroberfläche wiedergegeben werden. Manuelle Änderungen der Codedatei werden nicht im [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] angezeigt. In der Codedatei vorgenommene manuelle Änderungen werden überschrieben, wenn der Designer gespeichert und Code erneut generiert wird. Informationen zum Hinzufügen von Benutzercode und Erweitern der von generierten Klassen die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], finden Sie unter [Vorgehensweise: Erweitern von O/R-Designer erstellten Code](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Erstellen und Konfigurieren von DataContext
 Nach dem Hinzufügen einer **LINQ to SQL-Klassen** Element zu einem Projekt, und Öffnen der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], die leere Entwurfsoberfläche stellt ein leeres <xref:System.Data.Linq.DataContext> bereit für die Konfiguration. die <xref:System.Data.Linq.DataContext> wird mit den Verbindungsinformationen des ersten Elements, das auf die Entwurfsoberfläche gezogen wird konfiguriert... Deshalb wird die Klasse <xref:System.Data.Linq.DataContext> mithilfe der Verbindungsinformationen des ersten Elements konfiguriert, das auf der Entwurfsoberfläche abgelegt wird. Weitere Informationen zu den <xref:System.Data.Linq.DataContext> Klasse finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Erstellen von Entitätsklassen, die Datenbanktabellen und -ansichten zugeordnet sind
 Sie können Entitätsklassen, die zu Tabellen und Ansichten zugeordnet sind, durch Ziehen von Datenbanktabellen und-Sichten aus erstellen **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Wie im vorherigen Abschnitt angegeben die <xref:System.Data.Linq.DataContext> konfiguriert ist, mit der Verbindungsinformationen des ersten Elements, das auf die Entwurfsoberfläche gezogen wird. Wenn ein nachfolgendes Element mit einer anderen Verbindung dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] hinzugefügt wird, können Sie die Verbindung für <xref:System.Data.Linq.DataContext> ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von LINQ to SQL-Klassen, die Tabellen und Ansichten zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Erstellen von DataContext-Methoden, die gespeicherte Prozeduren und Funktionen aufrufen
 Sie erstellen <xref:System.Data.Linq.DataContext> Methoden, die aufgerufen werden (zugeordnet) gespeicherte Prozeduren und Funktionen durch Ziehen von **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Gespeicherte Prozeduren und Funktionen werden dem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] als Methoden vom <xref:System.Data.Linq.DataContext> hinzugefügt.

> [!NOTE]
>  Beim Ziehen von gespeicherten Prozeduren und Funktionen von **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methode unterscheidet sich abhängig davon, wo Sie das Element ablegen. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurieren von DataContext, um mithilfe von gespeicherten Prozeduren Daten zwischen Entitätsklassen und einer Datenbank zu speichern
 Wie bereits angemerkt wurde, können <xref:System.Data.Linq.DataContext>-Methoden erstellt werden, die gespeicherte Prozeduren und Funktionen aufrufen. Weiterhin können dem standardmäßigen [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Laufzeitverhalten auch gespeicherte Prozeduren zum Durchführen von Einfüge-, Update- und Löschvorgänge zugewiesen werden. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktionen zum Aktualisieren, Einfügen und Löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Vererbung und der O/R-Designer
 Wie andere Objekte können [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]-Klassen die Vererbung verwenden und aus anderen Klassen abgeleitet werden. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] unterstützt das häufig in relationalen Systemen implementierte Konzept der Vererbung einer einzelnen Tabelle. Weitere Informationen finden Sie unter [Vorgehensweise: Configure inheritance by using the O/R Designer (Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer)](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL-Abfragen
 Die Entitätsklassen erstellt die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] dienen zur Verwendung mit [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Weitere Informationen finden Sie unter [Vorgehensweise: Abfragen von Informationen](http://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Trennen des generierten DataContext und des Entitätsklassencodes in verschiedene Namespaces
 Die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] bietet die **Kontext Namespace** und **Entity Namespace** Eigenschaften für die <xref:System.Data.Linq.DataContext>. Mit diesen Eigenschaften wird festgelegt in welchen Namespace der <xref:System.Data.Linq.DataContext> und der Entitätsklassencode generiert werden. Standardmäßig sind diese Eigenschaften leer, und der <xref:System.Data.Linq.DataContext> und die Entitätsklassen werden in den Namespace der Anwendung generiert. Geben Sie einen Wert in die Eigenschaften **Context Namespace** und/oder **Entity Namespace** ein, um den Code in einem anderen Namespace als dem der Anwendung zu generieren.

## <a name="in-this-section"></a>In diesem Abschnitt
 [DataContext-Methoden (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) erläutert, welche <xref:System.Data.Linq.DataContext> Methoden sind und wie sie erstellt.

 [Datenklassenvererbung (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md) beschreibt das Konzept der Vererbung einer einzelnen Tabelle und die Implementierung in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Vorgehensweise: Erstellen von LINQ to SQL-Klassen zugeordnet, die mit Tabellen und Sichten (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) enthält Informationen zum Erstellen von Entitätsklassen, die Tabellen und Sichten in einer Datenbank zugeordnet sind.

 [Vorgehensweise: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) enthält Informationen zum Erstellen einer Beziehung zwischen [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] Entitätsklassen.

 [Vorgehensweise: Erstellen Sie DataContext-Methoden zugeordnet wird, um gespeicherte Prozeduren und Funktionen (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) beschreibt das Erstellen von <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren oder Funktionen ausgeführt, wenn sie aufgerufen werden.

 [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) beschreibt das Konfigurieren einer <xref:System.Data.Linq.DataContext> zum Verwenden gespeicherter Prozeduren beim Zurückspeichern von Daten aus Entitätsklassen Klassen, die in einer Datenbank zurück.

 [Vorgehensweise: Ändern des Rückgabetyps einer DataContext-Methode (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) beschreibt den Rückgabetyp einer <xref:System.Data.Linq.DataContext> Methode, um den Typ einer Entitätsklasse oder einen automatisch generierten Typ vom O/R-Designer erstellt werden.

 [Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen](../data-tools/how-to-add-validation-to-entity-classes.md) wird beschrieben, wie das Generieren partielle Methoden, mit denen bei eigenschaftenänderungen und Updates von Entitätsklassen Code hinzufügen können.

 [Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) wird beschrieben, wie aktivieren und deaktivieren Sie die automatische Umbenennung von Klassen, die hinzugefügt werden, die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Vorgehensweise: Konfigurieren der Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) beschreibt das Konfigurieren von Entitätsklassen, die mithilfe der Vererbung einer einzelnen Tabelle mit den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Vorgehensweise: Erweitern Sie die Code generiert, durch den O/R-Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) wird beschrieben, wie und wo Code hinzufügen, die nicht überschrieben wird, wenn Änderungen an Objekten im O/R-Designer Code neu generiert.

 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen, indem Sie mithilfe von Vererbung einer einzelnen Tabelle (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) enthält schrittweise Anleitungen zum Konfigurieren von Entitätsklassen, die mithilfe der Vererbung einer einzelnen Tabelle mit den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und delete-Verhalten von Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) enthält schrittweise Anweisungen zum Konfigurieren einer <xref:System.Data.Linq.DataContext> zum Verwenden gespeicherter Prozeduren beim Zurückspeichern von Daten aus Entitätsklassen Klassen, die in einer Datenbank zurück.

## <a name="reference-content"></a>Verweisen auf Inhalte
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [häufig gestellte Fragen](http://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Datenzugriff in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
