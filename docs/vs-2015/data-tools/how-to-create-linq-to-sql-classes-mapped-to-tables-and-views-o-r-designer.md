---
title: 'Vorgehensweise: Erstellen von LINQ to SQL Klassen, die Tabellen und Ansichten zugeordnet sind (O-R-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a63e81abcae508487afa40d0778c0f9e9b9caf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665923"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Vorgehensweise: Erstellen von LINQ to SQL-Klassen, die Tabellen und Ansichten zugeordnet sind (O/R-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ to SQL Klassen, die Datenbanktabellen und Sichten zugeordnet sind, werden als *Entitäts Klassen*bezeichnet. Die Entitätsklasse wird einem Datensatz zugeordnet, während die einzelnen Eigenschaften einer Entitätsklasse den jeweiligen Spalten eines Datensatzes zugeordnet werden. Erstellen Sie Entitäts Klassen, die auf Datenbanktabellen oder Sichten basieren, indem Sie Tabellen oder Sichten aus **Server-Explorer** / **Datenbank-Explorer** auf die [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)ziehen. Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] generiert die Klassen und wendet das spezifische [! Zu Aktivier LINQ to SQL Attribute [! LINQ to SQL-Funktionalität (die Daten Kommunikations-und Bearbeitungsfunktionen von <xref:System.Data.Linq.DataContext> ). Ausführliche Informationen zu [! LINQ to SQL-Klassen finden Sie [im LINQ to SQL-Objektmodell](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Ist ein einfaches objektrelationaler Mapper, da er nur 1:1-Zuordnungsbeziehungen unterstützt. Das heißt, dass eine Entitätsklasse nur über eine 1:1-Zuordnungsbeziehung zu einer Datenbanktabelle oder -ansicht verfügen kann. Eine komplexe Zuordnung, z. B. das Zuordnen einer Entitätsklasse zu mehreren Tabellen, wird nicht unterstützt. Sie können jedoch einer Ansicht, die mehrere zusammengehörige Tabellen verknüpft, eine Entitätsklasse zuordnen.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Erstellen von LINQ to SQL-Klassen, die Datenbanktabellen oder -ansichten zugeordnet sind
 Wenn Sie Tabellen oder Sichten aus **Server-Explorer** / **Datenbank-Explorer** auf das ziehen [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] <xref:System.Data.Linq.DataContext> , werden neben den Methoden, die zum Ausführen von Updates verwendet werden, auch Entitäts Klassen erstellt.

 Standardmäßig ist der [! LINQ to SQL Runtime erstellt eine Logik, um Änderungen von einer aktualisierbaren Entitäts Klasse wieder in der Datenbank zu speichern. Diese Logik basiert auf dem Schema der Tabelle (den Spaltendefinitionen und Primärschlüsselinformationen). Wenn Sie dieses Verhalten nicht wünschen, können Sie eine Entitäts Klasse so konfigurieren, dass Sie gespeicherte Prozeduren verwendet, um Einfügungen, Updates und Löschungen anstelle der Standardeinstellung [! LINQ to SQL Laufzeitverhalten. Weitere Informationen finden Sie unter Gewusst [wie: Zuweisen von gespeicherten Prozeduren zum Durchführen von Aktualisierungen, Einfügungen und Löschungen (O/R-Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>So erstellen Sie LINQ to SQL-Klassen, die Datenbanktabellen oder -ansichten zugeordnet sind

1. Erweitern Sie in **Server** / **Datenbank-Explorer** **Tabellen** oder **Sichten** , und suchen Sie die Datenbanktabelle oder-Sicht, die Sie in Ihrer Anwendung verwenden möchten.

2. Ziehen Sie die Tabelle oder die Ansicht auf den [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Eine Entitätsklasse wird erstellt und auf der Entwurfsoberfläche angezeigt. Die Entitätsklasse verfügt über Eigenschaften, die sich auf die Spalten in der ausgewählten Tabelle oder Ansicht beziehen.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Erstellen einer Objektdatenquelle und Anzeigen der Daten auf einem Formular
 Nachdem Sie Entitäts Klassen mithilfe von erstellt [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] haben, können Sie eine Objektdaten Quelle erstellen und das [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) mit den Entitäts Klassen auffüllen.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>So erstellen Sie eine Objektdatenquelle auf Grundlage von LINQ to SQL-Entitätsklassen

1. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**, um ein Projekt zu erstellen.

2. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

3. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

4. Klicken Sie auf der Seite **Datenquellentyp auswählen** auf **Objekt**, und klicken Sie dann auf **Weiter**.

5. Erweitern Sie die Knoten, suchen und wählen Sie die Klasse aus.

    > [!NOTE]
    > Wenn die Klasse **Customer** nicht verfügbar ist, beenden Sie den Assistenten, erstellen Sie das Projekt, und führen Sie den Assistenten erneut aus.

6. Klicken Sie auf **Fertig stellen**, um die Datenquelle zu erstellen, und fügen Sie die Entitätsklasse **Customer** zum Fenster **Datenquellen** hinzu.

7. Ziehen Sie Elemente aus dem Fenster **Datenquellen** auf ein Formular.

## <a name="see-also"></a>Weitere Informationen

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL Klassen (O-R-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [DataContext-Methoden (O/R-Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Vorgehensweise: Erstellen von DataContext-Methoden, die zu gespeicherten Prozeduren und Funktionen zugeordnet sind (O/R-Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Das LINQ to SQL-Objektmodell](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Exemplarische Vorgehensweise: Anpassen des Einfüge-, Update- und Löschverhaltens in Entitätsklassen](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Exemplarische Vorgehensweise: Hinzufügen einer Validierung zu Entitätsklassen](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Vorgehensweise: Erstellen einer Zuordnung (Beziehung) zwischen LINQ to SQL-Klassen (O/R-Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)