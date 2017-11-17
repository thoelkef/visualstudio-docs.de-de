---
title: Direkten Zugriff auf die Datenbank mit einem TableAdapter | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: bd8a4c54ba67af567e28e27e5d70d3576645f496
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Direkten Zugriff auf die Datenbank mit einem TableAdapter
Zusätzlich zu den `InsertCommand`, `UpdateCommand`, und `DeleteCommand`, TableAdapter-Erstellung Methoden, die direkt gegen die Datenbank ausgeführt werden können. Diese Methoden (`TableAdapter.Insert`, `TableAdapter.Update`, und `TableAdapter.Delete`) aufgerufen werden, um Daten direkt in der Datenbank zu bearbeiten.  
  
 Wenn Sie diese Methoden direkten erstellen möchten, legen Sie des TableAdapters `GenerateDbDirectMethods` Eigenschaft `false` in der **Eigenschaften** Fenster. Wenn alle Abfragen zu einem TableAdapter zusätzlich zur Hauptabfrage des TableAdapter hinzugefügt werden, sind sie eigenständigen Abfragen, die kein DbDirect-Methoden generieren.  
  
## <a name="send-commands-directly-to-a-database"></a>Senden Sie Befehle direkt in einer Datenbank  
 Rufen Sie die TableAdapter-DbDirect-Methode, die die Aufgabe ausführt, die Sie ausführen möchten.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Zum Einfügen neuer Datensätze direkt in einer Datenbank  
  
-   Rufen Sie die `Insert` -Methode, die Werte für jede Spalte als Parameter übergeben. Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel.  
  
    > [!NOTE]
    >  Instanziieren Sie den TableAdapter, die Sie verwenden möchten, wenn Sie keine Instanz zur Verfügung.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Zum Aktualisieren von Datensätzen direkt in einer Datenbank  
  
-   Rufen Sie die `Update` -Methode, die neuen und ursprünglichen Werte für jede Spalte als Parameter zu übergeben.  
  
    > [!NOTE]
    >  Instanziieren Sie den TableAdapter, die Sie verwenden möchten, wenn Sie keine Instanz zur Verfügung.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Zum Löschen von Datensätzen direkt aus einer Datenbank  
  
-   Rufen Sie die `Delete` -Methode auf und übergibt die Werte für jede Spalte als Parameter von der `Delete` Methode. Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel.  
  
    > [!NOTE]
    >  Instanziieren Sie den TableAdapter, die Sie verwenden möchten, wenn Sie keine Instanz zur Verfügung.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)