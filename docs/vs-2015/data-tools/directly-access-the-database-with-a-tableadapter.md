---
title: Direkter Zugriff auf die Datenbank mit einem TableAdapter | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 58500e59a624dac55824033b8b9667754a9040c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657372"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Direktes Zugreifen auf die Datenbank mit einem TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zusätzlich zu den `InsertCommand`, `UpdateCommand` und `DeleteCommand` werden TableAdapters mit Methoden erstellt, die direkt für die Datenbank ausgeführt werden können. Diese Methoden (`TableAdapter.Insert`, `TableAdapter.Update` und `TableAdapter.Delete`) können aufgerufen werden, um Daten direkt in der Datenbank zu bearbeiten.

 Wenn Sie diese direkten Methoden nicht erstellen möchten, legen Sie die `GenerateDbDirectMethods`-Eigenschaft des TableAdapter auf `false` im **Eigenschaften** Fenster fest. Wenn einer TableAdapter-Abfrage zusätzlich zur Haupt Abfrage des TableAdapters Abfragen hinzugefügt werden, handelt es sich hierbei um eigenständige Abfragen, die diese DBDirect-Methoden nicht generieren.

## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirekt zu einer Datenbank
 Nennen Sie die TableAdapter-DBDirect-Methode, die die Aufgabe ausführt, die Sie ausführen möchten.

#### <a name="to-insert-new-records-directly-into-a-database"></a>So fügen Sie neue Datensätze direkt in eine Datenbank ein

- Nennen Sie die `Insert`-Methode des TableAdapter, und übergeben Sie die Werte für jede Spalte als Parameter. Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel verwendet.

    > [!NOTE]
    > Wenn keine Instanz verfügbar ist, instanziieren Sie den TableAdapter, den Sie verwenden möchten.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

#### <a name="to-update-records-directly-in-a-database"></a>So aktualisieren Sie Datensätze direkt in einer Datenbank

- Nennen Sie die `Update`-Methode des TableAdapter, und übergeben Sie die neuen und ursprünglichen Werte für jede Spalte als Parameter.

    > [!NOTE]
    > Wenn keine Instanz verfügbar ist, instanziieren Sie den TableAdapter, den Sie verwenden möchten.

     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]

#### <a name="to-delete-records-directly-from-a-database"></a>So löschen Sie Datensätze direkt aus einer Datenbank

- Wenden Sie die `Delete`-Methode des TableAdapter an, und übergeben Sie die Werte für jede Spalte als Parameter der `Delete` Methode. Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel verwendet.

    > [!NOTE]
    > Wenn keine Instanz verfügbar ist, instanziieren Sie den TableAdapter, den Sie verwenden möchten.

     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]

## <a name="see-also"></a>Siehe auch
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
