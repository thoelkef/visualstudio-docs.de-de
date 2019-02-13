---
title: 'Vorgehensweise: Erstellen von LINQ to SQL-Klassen, die Tabellen und Ansichten zugeordnet sind (O/R-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 90f08715795a75a4a429ce16fdfcf24d06ba5843
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970594"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Vorgehensweise: Erstellen von LINQ to SQL-Klassen, die Tabellen und Ansichten zugeordnet sind (O/R-Designer)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Klassen, die Datenbanktabellen und -ansichten zugeordnet sind, werden als *Entitätsklassen* bezeichnet. Die Entitätsklasse wird einem Datensatz zugeordnet, während die einzelnen Eigenschaften einer Entitätsklasse den jeweiligen Spalten eines Datensatzes zugeordnet werden. Erstellen von Entitätsklassen, die auf die Datenbanktabellen oder-Ansichten basieren, durch Ziehen von Tabellen oder Sichten aus **Server-Explorer** oder **Datenbank-Explorer** auf die [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Die **O/R Designer** generiert die Klassen und wendet die spezifischen [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Attribute zu [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Funktionalität (die Datenkommunikations- und Bearbeitungsfunktionen von der <xref:System.Data.Linq.DataContext>). Ausführliche Informationen zu [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] finden Sie unter [das LINQ to SQL-Objektmodell](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> Die **O/R Designer** ist eine einfache objektrelationale Zuordnungen, da es nur 1:1-zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Eine komplexe Zuordnung, z. B. das Zuordnen einer Entitätsklasse zu mehreren Tabellen, wird nicht unterstützt. Sie können jedoch einer Ansicht, die mehrere zusammengehörige Tabellen verknüpft, eine Entitätsklasse zuordnen.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Erstellen von LINQ to SQL-Klassen, die Datenbanktabellen oder -ansichten zugeordnet sind

Ziehen von Tabellen oder Ansichten von **Server-Explorer** oder **Datenbank-Explorer** auf die **O/R Designer** erstellt Entitätsklassen zusätzlich zu den <xref:System.Data.Linq.DataContext> Methoden, die dienen zum Ausführen von Updates.

Standardmäßig erstellt die [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Laufzeit die Logik zum Speichern von in einer aktualisierbaren Entitätsklasse vorgenommenen Änderungen in der Datenbank. Diese Logik basiert auf dem Schema der Tabelle (den Spaltendefinitionen und Primärschlüsselinformationen). Wenn Sie dieses Verhalten nicht wünschen, können Sie eine Entitätsklasse konfigurieren, um anstelle des [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Laufzeitverhaltens gespeicherte Prozeduren zum Durchführen von Einfüge-, Update- und Löschvorgängen zu verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>So erstellen Sie LINQ to SQL-Klassen, die Datenbanktabellen oder -ansichten zugeordnet sind

1.  Erweitern Sie unter **Server** oder im **Datenbank-Explorer** den Knoten **Tabellen** oder **Ansichten**, und suchen Sie die Datenbanktabelle oder -ansicht, die Sie in Ihrer Anwendung verwenden möchten.

2.  Ziehen Sie die Tabelle oder Ansicht auf die **O/R Designer**.

     Eine Entitätsklasse wird erstellt und auf der Entwurfsoberfläche angezeigt. Die Entitätsklasse verfügt über Eigenschaften, die sich auf die Spalten in der ausgewählten Tabelle oder Ansicht beziehen.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Erstellen einer Objektdatenquelle und Anzeigen der Daten auf einem Formular

Nach der Erstellung von Entitätsklassen mithilfe der **O/R Designer**, können Sie eine Objektdatenquelle erstellen und füllen die [Fenster "Datenquellen"](add-new-data-sources.md#data-sources-window) mit den Entitätsklassen.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>So erstellen Sie eine Objektdatenquelle auf Grundlage von LINQ to SQL-Entitätsklassen

1.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**, um ein Projekt zu erstellen.

2.  Zum Öffnen der **Datenquellen** Fenster auf die **Daten** Menü klicken Sie auf **Datenquellen anzeigen**.

3.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

4.  Klicken Sie auf der Seite **Datenquellentyp auswählen** auf **Objekt**, und klicken Sie dann auf **Weiter**.

5.  Erweitern Sie die Knoten, suchen und wählen Sie die Klasse aus.

    > [!NOTE]
    > Wenn die Klasse **Customer** nicht verfügbar ist, beenden Sie den Assistenten, erstellen Sie das Projekt, und führen Sie den Assistenten erneut aus.

6.  Klicken Sie auf **Fertig stellen**, um die Datenquelle zu erstellen, und fügen Sie die Entitätsklasse **Customer** zum Fenster **Datenquellen** hinzu.

7.  Ziehen Sie Elemente aus dem Fenster **Datenquellen** auf ein Formular.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer) (Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O/R-Designer))](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext methods (O/R Designer) (DataContext-Methoden (O/R-Designer))](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Erstellen von DataContext-Methoden, die zu gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [The LINQ to SQL object model (Das LINQ to SQL-Objektmodell)](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Vorgehensweise: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R-Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)