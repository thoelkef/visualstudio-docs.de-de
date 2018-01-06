---
title: "Übersicht über Visual Studio-O/R-Designer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a160cce25814cd2e110f8896ed6752a18b5dd0da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>LINQ to SQL-Tools in Visual Studio
LINQ to SQL ist die erste objektrelationales Mapping-Technologie von Microsoft veröffentlicht wurden. Es funktioniert gut in grundlegende Szenarien und weiterhin in Visual Studio unterstützt werden, aber es ist nicht mehr in der aktiven Entwicklung. Verwenden Sie LINQ to SQL, wenn eine ältere Anwendung zu verwalten, die er bereits verwendet wird, oder in einfachen Anwendungen, die mithilfe von SQL Server und erfordern keine Zuordnung mit mehreren Tabellen. Neue Anwendungen sollten im Allgemeinen das Entity Framework verwenden, wenn eine Ebene objektrelationalen Mapper erforderlich ist.  
  
In Visual Studio erstellen Sie LINQ to SQL-Klassen, die SQL-Tabellen mithilfe der Object Relational Designer (O/R-Designer) darstellen.  
  
Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] verfügt über zwei verschiedene Bereiche auf seiner Entwurfsoberfläche: den Entitätenbereich auf der linken Seite und den Methodenbereich auf der rechten Seite. Der Entitätenbereich ist die Hauptentwurfsoberfläche, auf der Entitätsklassen, Zuordnungen und Vererbungshierarchien angezeigt werden. Der Methodenbereich ist die Entwurfsoberfläche, die zeigt die <xref:System.Data.Linq.DataContext> Methoden, die gespeicherten Prozeduren und Funktionen zugeordnet sind.  
  
Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] bietet eine visuelle Entwurfsoberfläche zum Erstellen von [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) Entitätsklassen und Zuordnungen (Beziehungen), die auf Objekte in einer Datenbank basieren. Mit anderen Worten: Der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] wird verwendet, um in einer Anwendung ein Objektmodell zu erstellen, das den Objekten in einer Datenbank entspricht. Außerdem generiert er einen stark typisierten <xref:System.Data.Linq.DataContext>, mit dem Daten an die Entitätsklassen gesendet und aus der Datenbank empfangen werden. Der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] stellt auch Funktionen bereit, um gespeicherte Prozeduren und Funktionen <xref:System.Data.Linq.DataContext>-Methoden zum Zurückgeben von Daten und Füllen von Entitätsklassen zuzuordnen. Abschließend bietet der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] die Möglichkeit, Vererbungsbeziehungen zwischen Entitätsklassen zu entwerfen.  
  
## <a name="opening-the-or-designer"></a>Öffnen des O/R-Designers  
 Um eine LINQ to SQL-Entität-Objektmodell zum Projekt hinzuzufügen, wählen **Projekt**, **neues Element hinzufügen** und wählen Sie dann **LINQ to SQL-Klassen** aus der Liste der Projektelemente:  
  
 ![LINQ to SQL-Klassen](../data-tools/media/raddata-linq-to-sql-classes.png "Raddata LINQ to SQL-Klassen")  
  
 Visual Studio erstellt eine DBML-Datei und der Projektmappe hinzugefügt. Dies ist die XML-Zuordnungsdatei und die zugehörigen Code-Dateien.  
  
 ![LINQ to SQL-Klassen im Projektmappen-Explorer](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "Raddata LINQ to SQL-Klassen im Projektmappen-Explorer")  
  
 Wenn Sie die DBML-Datei auswählen, zeigt Visual Studio die Oberfläche des O/R-Designers, die Ihnen ermöglicht, das Modell visuell zu erstellen. Die folgende Abbildung zeigt den Designer, nachdem die Northwind Customers und Orders-Tabellen aus Server-Explorer gezogen haben. Beachten Sie die Beziehung zwischen den Tabellen.  
  
 ![LINQ to SQL-Designer](../data-tools/media/raddata-linq-to-sql-designer.png "Raddata LINQ to SQL-Designer")  
  
> [!IMPORTANT]
>  Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ist eine einfache objektrelationale Zuordnungen, da er nur 1:1-zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Eine komplexe Zuordnung, z. B. das Zuordnen einer Entitätsklasse zu einer verknüpften Tabelle wird nicht unterstützt. Verwenden Sie das Entity Framework für komplexe Zuordnung. Darüber hinaus ist der Designer ein unidirektionaler Code-Generator. Das bedeutet, dass in der Codedatei nur Änderungen der Designeroberfläche wiedergegeben werden. Manuelle Änderungen der Codedatei werden nicht im [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] angezeigt. Änderungen, die Sie manuell in der Codedatei werden überschrieben, wenn der Designer gespeichert und Code neu generiert wird. Informationen zum Hinzufügen von Benutzercode und erweitern Sie die Klassen generiert werden, indem Sie die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], finden Sie unter [wie: Erweitern Code, die von O/R-Designer generiert](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Erstellen und Konfigurieren von DataContext  
 Nach dem Hinzufügen einer **LINQ to SQL-Klassen** Element zu einem Projekt, und Öffnen der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], die leere Entwurfsoberfläche stellt ein leeres <xref:System.Data.Linq.DataContext> bereit für die Konfiguration. die <xref:System.Data.Linq.DataContext> mit Verbindungsinformationen des ersten Elements, das auf die Entwurfsoberfläche gezogen wird konfiguriert... Aus diesem Grund die <xref:System.Data.Linq.DataContext> wird mithilfe der Verbindungsinformationen des ersten Elements auf der Entwurfsoberfläche abgelegt werden konfiguriert. Weitere Informationen zu den <xref:System.Data.Linq.DataContext> Klasse finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Erstellen von Entitätsklassen, die Datenbanktabellen und -ansichten zugeordnet sind  
 Erstellen Sie Entitätsklassen, die durch Ziehen von Datenbanktabellen und-Sichten aus Tabellen und Ansichten zugeordnet **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Wie im vorherigen Abschnitt angegeben die <xref:System.Data.Linq.DataContext> konfiguriert ist, mit der Verbindungsinformationen des ersten Elements, das auf die Entwurfsoberfläche gezogen wird. Wenn ein nachfolgendes Element mit einer anderen Verbindung dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] hinzugefügt wird, können Sie die Verbindung für <xref:System.Data.Linq.DataContext> ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von LINQ to SQL-Klassen, die mit Tabellen und Sichten (O/R-Designer) zugeordnet](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Erstellen von DataContext-Methoden, die gespeicherte Prozeduren und Funktionen aufrufen  
 Sie können erstellen <xref:System.Data.Linq.DataContext> Methoden, die aufgerufen werden (zugeordnet werden) gespeicherte Prozeduren und Funktionen von Drag & Drop aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Gespeicherte Prozeduren und Funktionen werden dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] als Methoden vom <xref:System.Data.Linq.DataContext> hinzugefügt.  
  
> [!NOTE]
>  Beim Ziehen von gespeicherten Prozeduren und Funktionen aus **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], der Rückgabetyp der generierten <xref:System.Data.Linq.DataContext> Methoden unterscheiden sich in Je nachdem, wo Sie das Element ablegen. Weitere Informationen finden Sie unter [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Konfigurieren von DataContext, um mithilfe von gespeicherten Prozeduren Daten zwischen Entitätsklassen und einer Datenbank zu speichern  
 Wie bereits angemerkt wurde, können <xref:System.Data.Linq.DataContext>-Methoden erstellt werden, die gespeicherte Prozeduren und Funktionen aufrufen. Weiterhin können dem standardmäßigen [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Laufzeitverhalten auch gespeicherte Prozeduren zum Durchführen von Einfüge-, Update- und Löschvorgänge zugewiesen werden. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Vererbung und der O/R-Designer  
 Wie andere Objekte können [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Klassen die Vererbung verwenden und aus anderen Klassen abgeleitet werden. Vererbungsbeziehungen werden in einer Datenbank auf verschiedene Arten erstellt. Der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] unterstützt das häufig in relationalen Systemen implementierte Konzept der Vererbung einer einzelnen Tabelle. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren der Vererbung mithilfe des O/R-Designers](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>LINQ to SQL-Abfragen  
 Die Entitätsklassen erstellt, indem die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] dienen zur Verwendung mit [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/). Weitere Informationen finden Sie unter [wie: Abfragen von Informationen](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Trennen des generierten DataContext und des Entitätsklassencodes in verschiedene Namespaces  
 Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] bietet die **Context Namespace** und **Entity Namespace** Eigenschaften für die <xref:System.Data.Linq.DataContext>. Mit diesen Eigenschaften wird festgelegt in welchen Namespace der <xref:System.Data.Linq.DataContext> und der Entitätsklassencode generiert werden. Standardmäßig sind diese Eigenschaften leer, und der <xref:System.Data.Linq.DataContext> und die Entitätsklassen werden in den Namespace der Anwendung generiert. Um den Code in einem Namespace als die Anwendung generieren, geben Sie einen Wert in der **Context Namespace** und/oder **Entity Namespace** Eigenschaften.
  
## <a name="reference-content"></a>Referenzmaterial
<xref:System.Linq>  
<xref:System.Data.Linq>  
  
## <a name="see-also"></a>Siehe auch
[LINQ to SQL ((.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)    
[Häufig gestellte Fragen ((.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions) 