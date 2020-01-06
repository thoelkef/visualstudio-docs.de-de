---
title: Speichern von Daten aus einem Objekt in einer Datenbank
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 509910730d4da095b6db622212716a8f958495d7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586262"
---
# <a name="save-data-from-an-object-to-a-database"></a>Speichern von Daten aus einem Objekt in einer Datenbank

Sie können Daten in Objekten in einer Datenbank speichern, indem Sie die Werte aus dem-Objekt an eine der DBDirect-Methoden des TableAdapter übergeben (z. b. `TableAdapter.Insert`). Weitere Informationen finden Sie unter [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Um Daten aus einer Auflistung von-Objekten zu speichern, durchlaufen Sie die Auflistung von-Objekten (z. b. eine for-Next-Schleife), und senden Sie die Werte für jedes Objekt mithilfe einer der `DBDirect` Methoden des TableAdapter an die Datenbank.

Standardmäßig werden `DBDirect` Methoden auf einem TableAdapter erstellt, der direkt für die Datenbank ausgeführt werden kann. Diese Methoden können direkt aufgerufen werden, und es ist nicht erforderlich, <xref:System.Data.DataSet>-oder <xref:System.Data.DataTable>-Objekten Änderungen abzugleichen, um Updates an eine Datenbank zu senden.

> [!NOTE]
> Wenn Sie einen TableAdapter konfigurieren, muss die Haupt Abfrage genügend Informationen für die zu erstellenden `DBDirect` Methoden bereitstellen. Wenn ein TableAdapter z. b. so konfiguriert ist, dass Daten aus einer Tabelle abgefragt werden, für die keine Primärschlüssel Spalte definiert ist, werden keine `DBDirect` Methoden generiert.

|TableAdapter-DBDirect-Methode|Beschreibung|
| - |-----------------|
|`TableAdapter.Insert`|Fügt einer Datenbank neue Datensätze hinzu und ermöglicht es Ihnen, einzelne Spaltenwerte als Methoden Parameter zu übergeben.|
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die `Update`-Methode übernimmt die ursprünglichen und neuen Spaltenwerte als Methoden Parameter. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden zum Aktualisieren dieses Datensatzes verwendet.<br /><br /> Die `TableAdapter.Update`-Methode wird auch verwendet, um Änderungen in einem Dataset an die Datenbank zurück zustimmen, indem ein <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>oder ein Array von <xref:System.Data.DataRow>s als Methoden Parameter verwendet wird.|
|`TableAdapter.Delete`|Löscht vorhandene Datensätze aus der Datenbank auf Grundlage der ursprünglichen Spaltenwerte, die als Methoden Parameter weitergegeben werden.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>So speichern Sie neue Datensätze aus einem Objekt in einer Datenbank

- Erstellen Sie die Datensätze, indem Sie die Werte an die `TableAdapter.Insert`-Methode übergeben.

     Im folgenden Beispiel wird ein neuer Kundendaten Satz in der `Customers` Tabelle erstellt, indem die Werte im `currentCustomer`-Objekt an die `TableAdapter.Insert`-Methode übergeben werden.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>So aktualisieren Sie vorhandene Datensätze von einem Objekt in eine Datenbank

- Ändern Sie die Datensätze, indem Sie die `TableAdapter.Update`-Methode aufrufen, die neuen Werte übergeben, um den Datensatz zu aktualisieren, und die ursprünglichen Werte übergeben, um den Datensatz zu suchen.

    > [!NOTE]
    > Das Objekt muss die ursprünglichen Werte beibehalten, um Sie an die `Update`-Methode zu übergeben. In diesem Beispiel werden Eigenschaften mit einem `orig`-Präfix verwendet, um die ursprünglichen Werte zu speichern.

     Im folgenden Beispiel wird ein vorhandener Datensatz in der `Customers` Tabelle aktualisiert, indem die neuen und ursprünglichen Werte im `Customer`-Objekt an die `TableAdapter.Update`-Methode übergeben werden.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>So löschen Sie vorhandene Datensätze aus einer Datenbank

- Löschen Sie die Datensätze, indem Sie die `TableAdapter.Delete`-Methode aufrufen und die ursprünglichen Werte übergeben, um den Datensatz zu suchen.

    > [!NOTE]
    > Das Objekt muss die ursprünglichen Werte beibehalten, um Sie an die `Delete`-Methode zu übergeben. In diesem Beispiel werden Eigenschaften mit einem `orig`-Präfix verwendet, um die ursprünglichen Werte zu speichern.

     Im folgenden Beispiel wird ein Datensatz aus der `Customers` Tabelle gelöscht, indem die ursprünglichen Werte im `Customer`-Objekt an die `TableAdapter.Delete`-Methode übergeben werden.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-security"></a>.NET-Sicherheit

Sie müssen über die Berechtigung verfügen, die ausgewählten `INSERT`, `UPDATE`oder `DELETE` in der-Tabelle in der-Datenbank auszuführen.

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
