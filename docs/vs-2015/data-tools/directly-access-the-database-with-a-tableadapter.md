---
title: Direktes Zugreifen auf die Datenbank mit einem TableAdapter | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 924a14cc3938420f32a1a2c25265ebe94e261b15
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431963"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Direktes Zugreifen auf die Datenbank mit einem TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zusätzlich zu den `InsertCommand`, `UpdateCommand`, und `DeleteCommand`, TableAdapter-Erstellung mit Methoden, die direkt in der Datenbank ausgeführt werden können. Diese Methoden (`TableAdapter.Insert`, `TableAdapter.Update`, und `TableAdapter.Delete`) aufgerufen werden, um Daten direkt in der Datenbank zu bearbeiten.  
  
 Wenn Sie nicht diese direkten Methoden erstellen möchten, legen Sie der TableAdapters `GenerateDbDirectMethods` Eigenschaft `false` in die **Eigenschaften** Fenster. Wenn alle Abfragen zu einem TableAdapter neben der Hauptabfrage des TableAdapter hinzugefügt werden, sind sie eigenständigen Abfragen, die kein DbDirect-Methoden generieren.  
  
## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly in einer Datenbank  
 Rufen Sie die TableAdapter-DbDirect-Methode, die Aufgabe ausführt, die Sie erreichen möchten.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Zum Einfügen neuer Datensätze direkt in eine Datenbank  
  
- Rufen Sie die `Insert` -Methode, die Werte für jede Spalte als Parameter übergeben. Im folgenden Verfahren wird die `Region` -Tabelle in der Northwind-Databaseas ein Beispiel.  
  
    > [!NOTE]
    > Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Zum Aktualisieren von Datensätzen, die direkt in einer Datenbank  
  
- Rufen Sie die `Update` -Methode, die neuen und ursprünglichen Werte für jede Spalte als Parameter übergeben.  
  
    > [!NOTE]
    > Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Zum Löschen von Datensätzen direkt aus einer Datenbank  
  
- Rufen Sie die `Delete` -Methode, die Werte für jede Spalte als Parameter übergeben die `Delete` Methode. Im folgenden Verfahren wird die `Region` -Tabelle in der Northwind-Databaseas ein Beispiel.  
  
    > [!NOTE]
    > Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Siehe auch  
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
