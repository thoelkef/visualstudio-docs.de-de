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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 22a2580809394ba1b41e7923f4f2df458d995a93
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750961"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Direktes Zugreifen auf die Datenbank mit einem TableAdapter

Zusätzlich zu den `InsertCommand`, `UpdateCommand`, und `DeleteCommand`, TableAdapter-Erstellung mit Methoden, die direkt in der Datenbank ausgeführt werden können. Sie können diese Methoden aufrufen (`TableAdapter.Insert`, `TableAdapter.Update`, und `TableAdapter.Delete`) zum Bearbeiten von Daten direkt in der Datenbank.

Wenn Sie nicht diese direkten Methoden erstellen möchten, legen Sie der TableAdapters `GenerateDbDirectMethods` Eigenschaft `false` in die **Eigenschaften** Fenster. Wenn alle Abfragen zu einem TableAdapter neben der Hauptabfrage des TableAdapter hinzugefügt werden, sind sie eigenständige-Abfragen, die diese kein generieren `DbDirect` Methoden.

## <a name="send-commands-directly-to-a-database"></a>Senden von Befehlen direkt in einer Datenbank

Rufen Sie die `DbDirect` -Methode, die vom Task ausgeführten Sie ausführen möchten.

### <a name="to-insert-new-records-directly-into-a-database"></a>Zum Einfügen neuer Datensätze direkt in eine Datenbank

-   Rufen Sie die `Insert` -Methode, die Werte für jede Spalte als Parameter übergeben. Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel.

    > [!NOTE]
    > Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Zum Aktualisieren von Datensätzen, die direkt in einer Datenbank

-   Rufen Sie die `Update` -Methode, die neuen und ursprünglichen Werte für jede Spalte als Parameter übergeben.

    > [!NOTE]
    > Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Zum Löschen von Datensätzen direkt aus einer Datenbank

-   Rufen Sie die `Delete` -Methode, die Werte für jede Spalte als Parameter übergeben die `Delete` Methode. Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel.

    > [!NOTE]
    > Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)