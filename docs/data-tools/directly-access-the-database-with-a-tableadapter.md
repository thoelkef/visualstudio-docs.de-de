---
title: Direktes Zugreifen auf die Datenbank mit einem TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8fe408c090dbdc2157cd52977d4bbed66cfe9109
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586691"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Direktes Zugreifen auf die Datenbank mit einem TableAdapter

Zusätzlich zu den `InsertCommand`, `UpdateCommand`und `DeleteCommand`werden TableAdapters mit Methoden erstellt, die direkt für die Datenbank ausgeführt werden können. Sie können diese Methoden (`TableAdapter.Insert`, `TableAdapter.Update`und `TableAdapter.Delete`) zum direkten Bearbeiten von Daten in der Datenbank aufzurufen.

Wenn Sie diese direkten Methoden nicht erstellen möchten, legen Sie die `GenerateDbDirectMethods`-Eigenschaft des TableAdapter auf `false` im **Eigenschaften** Fenster fest. Wenn einer TableAdapter-Abfrage zusätzlich zur Haupt Abfrage des TableAdapters Abfragen hinzugefügt werden, handelt es sich hierbei um eigenständige Abfragen, die diese `DbDirect` Methoden nicht generieren.

## <a name="send-commands-directly-to-a-database"></a>Direktes Senden von Befehlen an eine Datenbank

Nennen Sie die TableAdapter-`DbDirect` Methode, die die Aufgabe ausführt, die Sie ausführen möchten.

### <a name="to-insert-new-records-directly-into-a-database"></a>So fügen Sie neue Datensätze direkt in eine Datenbank ein

- Nennen Sie die `Insert`-Methode des TableAdapter, und übergeben Sie die Werte für jede Spalte als Parameter. Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel verwendet.

    > [!NOTE]
    > Wenn keine Instanz verfügbar ist, instanziieren Sie den TableAdapter, den Sie verwenden möchten.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>So aktualisieren Sie Datensätze direkt in einer Datenbank

- Nennen Sie die `Update`-Methode des TableAdapter, und übergeben Sie die neuen und ursprünglichen Werte für jede Spalte als Parameter.

    > [!NOTE]
    > Wenn keine Instanz verfügbar ist, instanziieren Sie den TableAdapter, den Sie verwenden möchten.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>So löschen Sie Datensätze direkt aus einer Datenbank

- Wenden Sie die `Delete`-Methode des TableAdapter an, und übergeben Sie die Werte für jede Spalte als Parameter der `Delete` Methode. Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel verwendet.

    > [!NOTE]
    > Wenn keine Instanz verfügbar ist, instanziieren Sie den TableAdapter, den Sie verwenden möchten.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
