---
title: Speichern von Daten aus einem Objekt in einer Datenbank | Microsoft-Dokumentation
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c1470c831177e74e7670d696b44fc2b0119a9a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607455"
---
# <a name="save-data-from-an-object-to-a-database"></a>Speichern von Daten aus einem Objekt in einer Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Daten in Objekten in einer Datenbank speichern, indem Sie die Werte aus dem-Objekt an eine der DBDirect-Methoden des TableAdapter übergeben (z `TableAdapter.Insert` . b.).

 Um Daten aus einer Auflistung von-Objekten zu speichern, durchlaufen Sie die Auflistung von-Objekten (z. b. eine for-Next-Schleife), und senden Sie die Werte für jedes Objekt mithilfe einer der DBDirect-Methoden des TableAdapter an die Datenbank.

 Standardmäßig werden DBDirect-Methoden auf einem TableAdapter erstellt, der direkt für die Datenbank ausgeführt werden kann. Diese Methoden können direkt aufgerufen werden und erfordern keine-oder-Objekte, um Änderungen abzugleichen, um <xref:System.Data.DataSet> <xref:System.Data.DataTable> Updates an eine Datenbank zu senden.

> [!NOTE]
> Wenn Sie einen TableAdapter konfigurieren, muss die Haupt Abfrage genügend Informationen bereitstellen, damit die DBDirect-Methoden erstellt werden können. Wenn ein TableAdapter z. b. so konfiguriert ist, dass Daten aus einer Tabelle abgefragt werden, für die keine Primärschlüssel Spalte definiert ist, werden keine DBDirect-Methoden generiert.

|TableAdapter-DBDirect-Methode|Beschreibung|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Fügt einer Datenbank neue Datensätze hinzu und ermöglicht es Ihnen, einzelne Spaltenwerte als Methoden Parameter zu übergeben.|
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die `Update` -Methode übernimmt die ursprünglichen und neuen Spaltenwerte als Methoden Parameter. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden zum Aktualisieren dieses Datensatzes verwendet.<br /><br /> Die- `TableAdapter.Update` Methode wird auch verwendet, um Änderungen in einem Dataset an die Datenbank zurück zustimmen, indem ein <xref:System.Data.DataSet> , <xref:System.Data.DataTable> , <xref:System.Data.DataRow> oder ein Array von <xref:System.Data.DataRow> s als Methoden Parameter verwendet wird.|
|`TableAdapter.Delete`|Löscht vorhandene Datensätze aus der Datenbank auf Grundlage der ursprünglichen Spaltenwerte, die als Methoden Parameter weitergegeben werden.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>So speichern Sie neue Datensätze aus einem Objekt in einer Datenbank

- Erstellen Sie die Datensätze, indem Sie die Werte an die- `TableAdapter.Insert` Methode übergeben.

     Im folgenden Beispiel wird ein neuer Kundendaten Satz in der- `Customers` Tabelle erstellt, indem die Werte des- `currentCustomer` Objekts an die-Methode übergeben werden `TableAdapter.Insert` .

     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>So aktualisieren Sie vorhandene Datensätze von einem Objekt in eine Datenbank

- Ändern Sie die Datensätze, indem Sie die- `TableAdapter.Update` Methode aufrufen, die neuen Werte übergeben, um den Datensatz zu aktualisieren, und die ursprünglichen Werte übergeben, um den Datensatz zu suchen.

    > [!NOTE]
    > Das Objekt muss die ursprünglichen Werte beibehalten, um Sie an die-Methode zu übergeben `Update` . In diesem Beispiel werden Eigenschaften mit einem `orig` Präfix verwendet, um die ursprünglichen Werte zu speichern.

     Im folgenden Beispiel wird ein vorhandener Datensatz in der- `Customers` Tabelle aktualisiert, indem die neuen und ursprünglichen Werte des- `Customer` Objekts an die-Methode übergeben werden `TableAdapter.Update` .

     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]

### <a name="to-delete-existing-records-from-a-database"></a>So löschen Sie vorhandene Datensätze aus einer Datenbank

- Löschen Sie die Datensätze `TableAdapter.Delete` , indem Sie die-Methode aufrufen und die ursprünglichen Werte übergeben, um den Datensatz zu suchen.

    > [!NOTE]
    > Das Objekt muss die ursprünglichen Werte beibehalten, um Sie an die-Methode zu übergeben `Delete` . In diesem Beispiel werden Eigenschaften mit einem `orig` Präfix verwendet, um die ursprünglichen Werte zu speichern.

     Im folgenden Beispiel wird ein Datensatz aus der- `Customers` Tabelle gelöscht, indem die ursprünglichen Werte des- `Customer` Objekts an die-Methode übergeben werden `TableAdapter.Delete` .

     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]

## <a name="net-framework-security"></a>.NET Framework-Sicherheit
 Sie müssen über die Berechtigung zum Ausführen der ausgewählten INSERT-, Update-oder DELETE-Berechtigung für die-Tabelle in der-Datenbank verfügen.

## <a name="see-also"></a>Weitere Informationen
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
