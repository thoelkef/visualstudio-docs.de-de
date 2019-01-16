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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 76b2673e81bcf15227195a299711848100bcd499
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968591"
---
# <a name="save-data-from-an-object-to-a-database"></a>Speichern von Daten aus einem Objekt in einer Datenbank

Sie können Daten in Objekten in einer Datenbank speichern, indem Sie die Werte aus dem Objekt eines TableAdapters-DBDirect-Methoden übergeben (z. B. `TableAdapter.Insert`). Weitere Informationen finden Sie unter [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Um Daten aus einer Auflistung von Objekten zu speichern, durchlaufen die Auflistung von Objekten (z. B. eine for-Next-Schleife), und senden Sie die Werte für jedes Objekt an die Datenbank mithilfe einer der des TableAdapter `DBDirect` Methoden.

In der Standardeinstellung `DBDirect` Methoden werden erstellt, auf einem TableAdapter, die direkt in der Datenbank ausgeführt werden kann. Diese Methoden können direkt aufgerufen werden und erfordern keine <xref:System.Data.DataSet> oder <xref:System.Data.DataTable> Objekte Änderungen abstimmen, um Updates in einer Datenbank zu senden.

> [!NOTE]
> Wenn Sie einen TableAdapter konfigurieren, muss die Hauptabfrage genügend Informationen für angeben der `DBDirect` Methoden erstellt werden. Z. B. wenn ein TableAdapter zum Abfragen von Daten aus einer Tabelle, die keine für eine primäre Schlüsselspalte definiert konfiguriert ist, generiert keine `DBDirect` Methoden.

|TableAdapter-DBDirect-Methode|Beschreibung|
| - |-----------------|
|`TableAdapter.Insert`|Fügt neue Datensätze in einer Datenbank und ermöglicht es Ihnen, einzelne Spaltenwerte als Methodenparameter übergeben.|
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die `Update` Methode übernimmt die Werte der ursprünglichen und neuen Spalte als Methodenparameter. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden verwendet, um diesen Datensatz aktualisieren.<br /><br /> Die `TableAdapter.Update` Methode dient auch zum Abstimmen von Änderungen in einem Dataset zurück an die Datenbank mithilfe einer <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, oder ein Array von <xref:System.Data.DataRow>s als Methodenparameter.|
|`TableAdapter.Delete`|Löscht den vorhandenen Datensätze aus der Datenbank, die basierend auf den ursprünglichen Spaltenwerte als Methodenparameter übergeben.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Um neue Datensätze aus einem Objekt in einer Datenbank zu speichern.

-   Erstellen Sie die Datensätze durch Übergeben der Werte, die `TableAdapter.Insert` Methode.

     Das folgende Beispiel erstellt einen neuer Kundendatensatz in der `Customers` Tabelle durch Übergeben der Werte in der `currentCustomer` -Objekt an die `TableAdapter.Insert` Methode.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Zum Aktualisieren vorhandener Datensätze aus einem Objekt in einer Datenbank

-   Ändern Sie die Datensätze durch Aufrufen der `TableAdapter.Update` -Methode, indem Sie die neuen Werte zur Aktualisierung des Datensatzes übergeben und in den ursprünglichen Werten den Datensatz gesucht.

    > [!NOTE]
    > Die ursprünglichen Werte beibehalten werden, um sie übergeben das Objekt muss die `Update` Methode. Dieses Beispiel verwendet die Eigenschaften mit einem `orig` Präfix, das die ursprünglichen Werte zu speichern.

     Das folgende Beispiel aktualisiert einen vorhandenen Datensatz in die `Customers` Tabelle übergeben Sie die neuen und ursprünglichen Werte in der `Customer` -Objekt an die `TableAdapter.Update` Methode.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>So löschen Sie vorhandene Datensätze aus einer Datenbank

-   Löschen Sie die Datensätze durch Aufrufen der `TableAdapter.Delete` -Methode und übergeben die ursprünglichen Werte den Datensatz gesucht.

    > [!NOTE]
    > Die ursprünglichen Werte beibehalten werden, um sie übergeben das Objekt muss die `Delete` Methode. Dieses Beispiel verwendet die Eigenschaften mit einem `orig` Präfix, das die ursprünglichen Werte zu speichern.

     Das folgende Beispiel löscht einen Datensatz aus der `Customers` Tabelle übergeben Sie die ursprünglichen Werte in der `Customer` -Objekt an die `TableAdapter.Delete` Methode.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>.NET Framework-Sicherheit

Sie benötigen die Berechtigung zum Ausführen der ausgewählten `INSERT`, `UPDATE`, oder `DELETE` für die Tabelle in der Datenbank.

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)