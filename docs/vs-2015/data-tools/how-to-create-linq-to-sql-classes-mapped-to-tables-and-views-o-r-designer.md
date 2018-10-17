---
title: 'Gewusst wie: Erstellen von LINQ to SQL-Klassen zugeordnet, die mit Tabellen und Sichten (O / R-Designer) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 550fc362cf1652df48e029461a4d5fbdc6f04006
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269532"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Gewusst wie: Erstellen von LINQ to SQL-Klassen zugeordnet, die mit Tabellen und Sichten (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ to SQL-Klassen, die Datenbanktabellen und-Ansichten zugeordnet sind, heißen *Entitätsklassen*. Die Entitätsklasse wird einem Datensatz zugeordnet, während die einzelnen Eigenschaften einer Entitätsklasse den jeweiligen Spalten eines Datensatzes zugeordnet werden. Erstellen von Entitätsklassen, die auf die Datenbanktabellen oder-Ansichten basieren, durch Ziehen von Tabellen oder Sichten aus **Server-Explorer**/**Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] generiert die Klassen und wendet die spezifischen [! LINQ auf SQL-Attribute, um ermöglichen [! LINQ zu SQL-Funktionen (die Datenkommunikations- und Bearbeitungsfunktionen von der <xref:System.Data.Linq.DataContext>). Ausführliche Informationen zu [! LINQ to SQL-Klassen finden Sie unter [das LINQ to SQL-Objektmodell](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> Die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ist eine einfache objektrelationale Zuordnungen, da es nur 1:1-zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Eine komplexe Zuordnung, z. B. das Zuordnen einer Entitätsklasse zu mehreren Tabellen, wird nicht unterstützt. Sie können jedoch einer Ansicht, die mehrere zusammengehörige Tabellen verknüpft, eine Entitätsklasse zuordnen.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Erstellen von LINQ to SQL-Klassen, die Datenbanktabellen oder -ansichten zugeordnet sind
 Ziehen von Tabellen oder Ansichten von **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] erstellt Entitätsklassen zusätzlich zu den <xref:System.Data.Linq.DataContext> Methoden, die für die verwendet werden Ausführen von Updates.

 In der Standardeinstellung der [! LINQ to SQL Laufzeit erstellt die Logik, um die Änderungen zu einer aktualisierbaren Entitätsklasse zurück in die Datenbank zu speichern. Diese Logik basiert auf dem Schema der Tabelle (den Spaltendefinitionen und Primärschlüsselinformationen). Wenn Sie dieses Verhalten nicht wünschen, können eine Entitätsklasse zur Verwendung gespeicherter Prozeduren zur Durchführung von Einfügungen, Updates, konfigurieren und löscht, statt das [! LINQ to SQL-Laufzeitverhalten. Weitere Informationen finden Sie unter [Vorgehensweise: Zuweisen von gespeicherten Prozeduren zum Ausführen von Updates, einfügungen und löschen (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>So erstellen Sie LINQ to SQL-Klassen, die Datenbanktabellen oder -ansichten zugeordnet sind

1.  In **Server**/**Datenbank-Explorer**, erweitern Sie **Tabellen** oder **Ansichten** und suchen Sie die Datenbanktabelle oder anzeigen, Sie möchten Um in Ihrer Anwendung verwenden zu können.

2.  Ziehen Sie die Tabelle oder die Ansicht auf den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Eine Entitätsklasse wird erstellt und auf der Entwurfsoberfläche angezeigt. Die Entitätsklasse verfügt über Eigenschaften, die sich auf die Spalten in der ausgewählten Tabelle oder Ansicht beziehen.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Erstellen einer Objektdatenquelle und Anzeigen der Daten auf einem Formular
 Nach der Erstellung von Entitätsklassen mithilfe der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], können Sie eine Objektdatenquelle erstellen und füllen die [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) mit den Entitätsklassen.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>So erstellen Sie eine Objektdatenquelle auf Grundlage von LINQ to SQL-Entitätsklassen

1.  Auf der **erstellen** Menü klicken Sie auf **Projektmappe** zum Erstellen Ihres Projekts.

2.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

3.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

4.  Klicken Sie auf **Objekt** auf die **wählen Sie einen Datenquellentyp** Seite, und klicken Sie dann auf **Weiter**.

5.  Erweitern Sie die Knoten, suchen und wählen Sie die Klasse aus.

    > [!NOTE]
    > Wenn die **Kunden** Klasse ist nicht verfügbar, den Assistenten abbrechen, erstellen Sie das Projekt und führen Sie den Assistenten erneut aus.

6.  Klicken Sie auf **Fertig stellen** zum Erstellen der Datenquelle und Hinzufügen der **Kunden** Entitätsklasse, um die **Datenquellen** Fenster.

7.  Ziehen Sie Elemente aus der **Datenquellen** auf das Formular.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Erstellen von DataContext-Methoden, die zu gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Das LINQ to SQL-Objektmodell](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Exemplarische Vorgehensweise: Hinzufügen einer Validierung zu Entitätsklassen](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Vorgehensweise: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R-Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)