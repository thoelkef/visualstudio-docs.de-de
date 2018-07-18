---
title: 'Vorgehensweise: Erstellen von LINQ to SQL-Klassen zugeordnet, die mit Tabellen und Sichten (O-R-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b81d67d6897826ab2f6de1e3b48663b18bffdb1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924634"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Vorgehensweise: Erstellen von LINQ to SQL-Klassen zugeordnet, die mit Tabellen und Sichten (O/R-Designer)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Klassen, Datenbanktabellen und-Ansichten zugeordnet sind, heißen *Entitätsklassen*. Die Entitätsklasse wird einem Datensatz zugeordnet, während die einzelnen Eigenschaften einer Entitätsklasse den jeweiligen Spalten eines Datensatzes zugeordnet werden. Erstellen von Entitätsklassen, die auf die Datenbanktabellen oder-Ansichten basieren, ziehen Sie Tabellen oder Sichten aus **Server-Explorer**/**Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] generiert die Klassen und wendet die spezifischen [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Attribute ermöglichen [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Funktionalität (die Datenkommunikations- und Bearbeitungsfunktionen von der <xref:System.Data.Linq.DataContext>). Ausführliche Informationen zu [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Klassen, finden Sie unter [das LINQ to SQL-Objektmodell](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
>  Die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ist eine einfache objektrelationale Zuordnungen, da er nur 1:1-zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Eine komplexe Zuordnung, z. B. das Zuordnen einer Entitätsklasse zu mehreren Tabellen, wird nicht unterstützt. Sie können jedoch einer Ansicht, die mehrere zusammengehörige Tabellen verknüpft, eine Entitätsklasse zuordnen.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Erstellen von LINQ to SQL-Klassen, die Datenbanktabellen oder -ansichten zugeordnet sind
 Ziehen Sie Tabellen oder Sichten von **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] erstellt Entitätsklassen zusätzlich zu den <xref:System.Data.Linq.DataContext> Methoden, die für verwendet werden Ausführen von Updates.

 Standardmäßig erstellt die [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Laufzeit die Logik zum Speichern von in einer aktualisierbaren Entitätsklasse vorgenommenen Änderungen in der Datenbank. Diese Logik basiert auf dem Schema der Tabelle (den Spaltendefinitionen und Primärschlüsselinformationen). Wenn Sie dieses Verhalten nicht wünschen, können Sie eine Entitätsklasse konfigurieren, um anstelle des [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]-Laufzeitverhaltens gespeicherte Prozeduren zum Durchführen von Einfüge-, Update- und Löschvorgängen zu verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>So erstellen Sie LINQ to SQL-Klassen, die Datenbanktabellen oder -ansichten zugeordnet sind

1.  In **Server**/**Datenbank-Explorer**, erweitern Sie **Tabellen** oder **Ansichten** und suchen Sie die Datenbanktabelle oder -Ansicht, werden sollen in der Anwendung verwenden zu können.

2.  Ziehen Sie die Tabelle oder die Ansicht auf den [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

     Eine Entitätsklasse wird erstellt und auf der Entwurfsoberfläche angezeigt. Die Entitätsklasse verfügt über Eigenschaften, die sich auf die Spalten in der ausgewählten Tabelle oder Ansicht beziehen.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Erstellen einer Objektdatenquelle und Anzeigen der Daten auf einem Formular
 Nach der Erstellung von Entitätsklassen mithilfe der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], können Sie eine Objektdatenquelle erstellen und Auffüllen der [Datenquellenfenster](add-new-data-sources.md) mit den Entitätsklassen.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>So erstellen Sie eine Objektdatenquelle auf Grundlage von LINQ to SQL-Entitätsklassen

1.  Auf der **erstellen** Menü klicken Sie auf **Projektmappe** zur Erstellung des Projekts.

2.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

3.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

4.  Klicken Sie auf **Objekt** auf die **wählen Sie einen Datenquellentyp** Seite, und klicken Sie dann auf **Weiter**.

5.  Erweitern Sie die Knoten, suchen und wählen Sie die Klasse aus.

    > [!NOTE]
    >  Wenn die **Kunden** Klasse ist nicht verfügbar, beenden Sie den Assistenten, erstellen Sie das Projekt und führen Sie den Assistenten erneut aus.

6.  Klicken Sie auf **Fertig stellen** zum Erstellen der Datenquelle und Hinzufügen der **Kunden** Entitätsklasse, die **Datenquellen** Fenster.

7.  Ziehen Sie Elemente aus der **Datenquellen** auf das Formular.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O-R-Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Erstellen von DataContext-Methoden zugeordnet werden, um gespeicherte Prozeduren und Funktionen (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Das LINQ to SQL-Objektmodell](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Vorgehensweise: erstellen eine Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R-Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)