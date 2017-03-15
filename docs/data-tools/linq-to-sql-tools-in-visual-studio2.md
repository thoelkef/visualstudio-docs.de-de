---
title: "LINQ to SQL-Tools in Visual Studio2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# LINQ to SQL-Tools in Visual Studio
LINQ to SQL ist die erste objektrelationales Mapping-Technologie von Microsoft veröffentlicht. Es eignet sich für einfache Szenarien und weiterhin in Visual Studio unterstützt werden, aber es ist nicht mehr aktiv weiterentwickelt. Verwenden Sie LINQ to SQL, wenn eine ältere Anwendung beibehalten, die bereits verwendet wird, oder in einfache Anwendung, die SQL Server verwenden und müssen nicht mit mehreren Tabellen zuordnen. Im Allgemeinen sollten neue Applikationen Entity Framework verwenden, wenn eine Ebene objektrelationale Zuordnung erforderlich ist.  
  
 In Visual Studio erstellen Sie LINQ to SQL-Klassen, die darstellen, SQL-Tabellen mithilfe der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] verfügt über zwei verschiedene Bereiche auf seiner Entwurfsoberfläche: den Entitätenbereich auf der linken Seite und den Methodenbereich auf der rechten Seite. Der Entitätenbereich ist die Hauptentwurfsoberfläche, auf der Entitätsklassen, Zuordnungen und Vererbungshierarchien angezeigt werden. Der Methodenbereich ist die Entwurfsoberfläche, die zeigt die <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind.  
  
 Die [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) bietet eine visuelle Entwurfsoberfläche zum Erstellen von [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) Entitätsklassen und Zuordnungen (Beziehungen), die auf Objekte in einer Datenbank basieren. Mit anderen Worten: Der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] wird verwendet, um in einer Anwendung ein Objektmodell zu erstellen, das den Objekten in einer Datenbank entspricht. Außerdem generiert er einen stark typisierten <xref:System.Data.Linq.DataContext> der zum Senden und Empfangen von Daten zwischen den Entitätsklassen und der Datenbank verwendet wird. Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] auch bietet Funktionen zum Zuordnen von gespeicherter Prozeduren und Funktionen <xref:System.Data.Linq.DataContext> -Methoden zum Zurückgeben von Daten und Füllen von Entitätsklassen. Abschließend bietet der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] die Möglichkeit, Vererbungsbeziehungen zwischen Entitätsklassen zu entwerfen.  
  
## <a name="opening-the-or-designer"></a>Öffnen des O/R-Designers  
 Um eine LINQ to SQL-Entität-Modell dem Projekt hinzuzufügen, wählen **Projekt &#124; Neues Element hinzufügen** und wählen Sie dann  **LINQ to SQL Classes** aus der Liste der Projektelemente:  
  
 ![LINQ to SQL-Klassen](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL Classes")  
  
 Visual Studio erstellt eine DBML-Datei und der Projektmappe hinzugefügt. Dies ist die XML-Zuordnungsdatei und die zugehörige Code-Dateien.  
  
 ![LINQ to SQL-Klassen im Projektmappen-Explorer](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes in Solution Explorer")  
  
 Wenn Sie die DBML-Datei auswählen, zeigt Visual Studio die O/R-Designeroberfläche, die Sie das Modell visuell erstellen kann. Die folgende Abbildung zeigt den Designer nach Northwind Customers und Orders-Tabellen im Server-Explorer gezogen haben. Beachten Sie die Beziehung zwischen den Tabellen.  
  
 ![LINQ to SQL-Designer](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")  
  
> [!IMPORTANT]
>  Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ist eine einfache objektrelationale Zuordnungen, da er nur die 1:1-zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Eine komplexe Zuordnung, z. B. das Zuordnen einer Entitätsklasse zu einer verknüpften Tabelle, wird nicht unterstützt. Verwenden Sie das Entity Framework für komplexe Zuordnung. Darüber hinaus ist der Designer ein unidirektionaler Code-Generator. Das bedeutet, dass in der Codedatei nur Änderungen der Designeroberfläche wiedergegeben werden. Manuelle Änderungen der Codedatei werden nicht im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] angezeigt. Änderungen, die Sie manuell in der Codedatei werden überschrieben, wenn im Designer gespeichert und Code erneut generiert wird. Informationen zum Hinzufügen von Benutzercode und Erweitern der von generierte Klassen der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], finden Sie unter [Gewusst wie: Erweitern Code vom O/R-Designer generiert](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Erstellen und Konfigurieren von DataContext  
 Nach dem Hinzufügen einer **LINQ to SQL-Klassen** Element zu einem Projekt und öffnen Sie die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], die leere Entwurfsoberfläche stellt ein leeres <xref:System.Data.Linq.DataContext> konfiguriert werden kann. die <xref:System.Data.Linq.DataContext> mit Verbindungsinformationen des ersten Elements, das auf die Entwurfsoberfläche gezogen wird konfiguriert... Aus diesem Grund die <xref:System.Data.Linq.DataContext> wird mithilfe der Verbindungsinformationen des ersten auf die Entwurfsoberfläche gezogenen Elements konfiguriert. Weitere Informationen zu den <xref:System.Data.Linq.DataContext> Klasse finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Erstellen von Entitätsklassen, die Datenbanktabellen und -ansichten zugeordnet sind  
 Sie können Entitätsklassen erstellen zugeordnet, Tabellen und Sichten durch Ziehen von Tabellen und Sichten aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Wie im vorherigen Abschnitt der <xref:System.Data.Linq.DataContext> konfiguriert ist, mit Verbindungsinformationen des ersten Elements, das auf die Entwurfsoberfläche gezogen wird. Wenn ein nachfolgendes Element mit einer anderen Verbindung hinzugefügt wird der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], Sie können ändern, dass die Verbindung für die <xref:System.Data.Linq.DataContext>. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von LINQ to SQL-Klassen zu Tabellen und Ansichten (O/R-Designer) zugeordnet](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Erstellen von DataContext-Methoden, die gespeicherte Prozeduren und Funktionen aufrufen  
 Sie erstellen <xref:System.Data.Linq.DataContext> Methoden, die aufgerufen werden (zugeordnet) gespeicherte Prozeduren und Funktionen durch Ziehen von **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Gespeicherte Prozeduren und Funktionen hinzugefügt werden die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] als Methoden der <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  Beim Ziehen von gespeicherten Prozeduren und Funktionen von **Server-Explorer**/**Datenbank-Explorer** auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], den Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> -Methode ist davon abhängig, in dem Sie das Element ablegen. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurieren von DataContext, um mithilfe von gespeicherten Prozeduren Daten zwischen Entitätsklassen und einer Datenbank zu speichern  
 Wie bereits erwähnt, können <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen aufrufen. Weiterhin können dem standardmäßigen [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Laufzeitverhalten auch gespeicherte Prozeduren zum Durchführen von Einfüge-, Update- und Löschvorgänge zugewiesen werden. Weitere Informationen finden Sie unter [Gewusst wie: Zuweisen von gespeicherten Prozeduren zum Aktualisieren, einfügen und löschen (O/R-Designer) ausführen](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Vererbung und der O/R-Designer  
 Wie andere Objekte können [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Klassen die Vererbung verwenden und aus anderen Klassen abgeleitet werden. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] unterstützt das häufig in relationalen Systemen implementierte Konzept der Vererbung einer einzelnen Tabelle. Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren von Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>LINQ to SQL-Abfragen  
 Die Entitätsklassen erstellt, indem die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] dienen zur Verwendung mit [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md). Weitere Informationen finden Sie unter [Gewusst wie: Abfragen von Informationen](../Topic/How%20to:%20Query%20for%20Information.md).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Trennen des generierten DataContext und des Entitätsklassencodes in verschiedene Namespaces  
 Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] enthält die **Context Namespace** und **Entity Namespace** Eigenschaften für die <xref:System.Data.Linq.DataContext>. Diese Eigenschaften bestimmen, welchen Namespace der <xref:System.Data.Linq.DataContext> und der Entitätsklassencode generiert werden. Standardmäßig sind diese Eigenschaften leer und die <xref:System.Data.Linq.DataContext> und Entitätsklassen werden in den Namespace der Anwendung generiert. Um den Code in einem anderen Namespace als dem der Anwendung zu generieren, geben Sie einen Wert in der **Kontext Namespace** und/oder **Entity Namespace** Eigenschaften.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)  
 Erläutert, was <xref:System.Data.Linq.DataContext> Methoden sind und wie Sie diese erstellen.  
  
 [Datenklassenvererbung (O/R-Designer)](../data-tools/data-class-inheritance-o-r-designer.md)  
 Beschreibt den Begriff der Vererbung für eine einzelne Tabelle und dessen Implementierung im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Gewusst wie: Erstellen von LINQ to SQL-Klassen zugeordnet werden, die Tabellen und Ansichten (O/R-Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)  
 Beschreibt das Erstellen von Entitätsklassen, die Tabellen und Ansichten in einer Datenbank zugeordnet sind.  
  
 [Gewusst wie: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R-Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)  
 Beschreibt das Erstellen einer Beziehung zwischen [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Entitätsklassen.  
  
 [Gewusst wie: Erstellen von DataContext-Methoden zugeordnet, gespeicherte Prozeduren und Funktionen (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)  
 Beschreibt das Erstellen von <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren oder Funktionen ausführen, wenn sie aufgerufen werden.  
  
 [Gewusst wie: Zuweisen von gespeicherten Prozeduren zum Aktualisieren, einfügen und löschen (O/R-Designer) ausführen.](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
 Beschreibt das Konfigurieren einer <xref:System.Data.Linq.DataContext> zur Verwendung gespeicherter Prozeduren beim Zurückspeichern von Daten aus Entitätsklassen Klassen, die in einer Datenbank zurück.  
  
 [Gewusst wie: Ändern des Rückgabetyps einer DataContext-Methode (O/R-Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)  
 Beschreibt das Festlegen des Rückgabetyps einer <xref:System.Data.Linq.DataContext> Methode, die den Typ einer Entitätsklasse oder einen automatisch generierten Typ vom O/R-Designer erstellt werden.  
  
 [Gewusst wie: Hinzufügen von Validierung zu Entitätsklassen](../data-tools/how-to-add-validation-to-entity-classes.md)  
 Beschreibt das Generieren partieller Methoden, mit denen Sie während der Durchführung von Eigenschaftenänderungen und Updates von Entitätsklassen Code hinzufügen können.  
  
 [Gewusst wie: Aktivieren/Deaktivieren der Pluralisierung (O/R-Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)  
 Beschreibt, wie die automatische Umbenennung von Klassen, die zu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] hinzugefügt werden, aktiviert bzw. deaktiviert werden kann.  
  
 [Gewusst wie: Konfigurieren von Vererbung mit dem O/R-Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)  
 Beschreibt, wie Entitätsklassen, die Vererbung für eine einzelne Tabelle verwenden, mit dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] konfiguriert werden.  
  
 [Gewusst wie: Erweitern von O/R-Designer generierten Code](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md)  
 Beschreibt das Hinzufügen von Code, der nicht überschrieben wird, wenn durch Änderungen an Objekten im O/R-Designer Code neu generiert wird.  
  
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen mithilfe von Vererbung einer einzelnen Tabelle (O/R-Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)  
 Bietet schrittweise Anweisungen zur Konfiguration von Entitätsklassen, die Vererbung für eine einzelne Tabelle verwenden, mithilfe von [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Exemplarische Vorgehensweise: Anpassen das Einfügen, aktualisieren und Löschen von Verhalten von Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
 Bietet eine schrittweise Anleitung zum Konfigurieren einer <xref:System.Data.Linq.DataContext> zur Verwendung gespeicherter Prozeduren beim Zurückspeichern von Daten aus Entitätsklassen Klassen, die in einer Datenbank zurück.  
  
## <a name="reference-content"></a>Referenzmaterial  
 <xref:System.Linq>  
  
 <xref:System.Data.Linq>  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Database Tools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Häufig gestellte Fragen](../Topic/Frequently%20Asked%20Questions.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)