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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 641b598eb855fb1f2c3a7ca38d966630fbac15bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="save-data-from-an-object-to-a-database"></a>Speichern von Daten aus einem Objekt in einer Datenbank
Sie können Daten in Objekten in einer Datenbank speichern, indem Sie die Werte aus dem Objekt in eines der TableAdapter-DBDirect-Methoden übergeben (z. B. `TableAdapter.Insert`). Weitere Informationen finden Sie unter [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

 Zum Speichern von Daten aus einer Auflistung von Objekten durchläuft die Auflistung von Objekten (z. B. eine Schleife für Weiter), und senden Sie die Werte für jedes Objekt in der Datenbank mithilfe TableAdapters-DBDirect-Methoden.

 Standardmäßig werden DBDirect-Methoden auf einem TableAdapter erstellt, die direkt gegen die Datenbank ausgeführt werden können. Diese Methoden können direkt aufgerufen werden und erfordern keine <xref:System.Data.DataSet> oder <xref:System.Data.DataTable> Objekte Änderungen abstimmen, um Updates an einer Datenbank zu senden.

> [!NOTE]
>  Wenn Sie einen TableAdapter konfigurieren, muss die Hauptabfrage genügend Informationen für die DBDirect-Methoden zu erstellenden angeben. Z. B. wenn ein TableAdapter zum Abfragen von Daten aus einer Tabelle, die über keine Primärschlüsselspalte definiert konfiguriert ist, wird er nicht DBDirect-Methoden generiert.

|TableAdapter-DBDirect-Methode|Beschreibung|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Fügt neue Datensätze zu einer Datenbank und ermöglicht es Ihnen, die Werte einzelner Spalten als Methodenparameter übergeben.|
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die `Update` Methode nimmt der ursprüngliche und die neue Spaltenwerte als Methodenparameter. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden verwendet, um diesen Datensatz zu aktualisieren.<br /><br /> Die `TableAdapter.Update` Methode dient auch zum Abstimmen von Änderungen in einem Dataset zurück an die Datenbank ergreifen Sie hierzu eine <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, oder ein Array von <xref:System.Data.DataRow>s als Methodenparameter.|
|`TableAdapter.Delete`|Löscht vorhandene Datensätze aus der Datenbank, basierend auf den ursprünglichen Spaltenwerte als Methodenparameter übergeben.|

### <a name="to-save-new-records-from-an-object-to-a-database"></a>Um neue Datensätze aus einem Objekt in einer Datenbank zu speichern.

-   Erstellen Sie die Datensätze durch Übergeben der Werte, die `TableAdapter.Insert` Methode.

     Im folgenden Beispiel wird einen neuer Kundendatensatz in der `Customers` Tabelle durch Übergeben der Werte in der `currentCustomer` -Objekt an die `TableAdapter.Insert` Methode.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Zum Aktualisieren vorhandener Datensätze aus einem Objekt in einer Datenbank

-   Ändern Sie die Datensätze durch Aufrufen der `TableAdapter.Update` Methode, indem Sie die neuen Werte zur Aktualisierung des Datensatzes übergeben und in die ursprünglichen Werte, um den Datensatz zu suchen.

    > [!NOTE]
    >  Das Objekt muss die ursprünglichen Werte beibehalten, damit sie zum Übergeben der `Update` Methode. Dieses Beispiel verwendet die Eigenschaften mit einem `orig` Präfix, das die ursprünglichen Werte zu speichern.

     Das folgende Beispiel aktualisiert einen vorhandenen Datensatz in der `Customers` Tabelle durch Übergeben der neuen und ursprünglichen Werte in der `Customer` -Objekt an die `TableAdapter.Update` Methode.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

### <a name="to-delete-existing-records-from-a-database"></a>So löschen Sie vorhandene Datensätze aus einer Datenbank

-   Löschen Sie die Datensätze durch Aufrufen der `TableAdapter.Delete` -Methode und übergeben die ursprünglichen Werte, um den Datensatz zu suchen.

    > [!NOTE]
    >  Das Objekt muss die ursprünglichen Werte beibehalten, damit sie zum Übergeben der `Delete` Methode. Dieses Beispiel verwendet die Eigenschaften mit einem `orig` Präfix, das die ursprünglichen Werte zu speichern.

     Das folgende Beispiel löscht einen Datensatz aus der `Customers` Tabelle übergeben die ursprünglichen Werte in der `Customer` -Objekt an die `TableAdapter.Delete` Methode.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>.NET Framework-Sicherheit
 Sie benötigen die Berechtigung zum Ausführen der ausgewählten INSERT-, Update- oder DELETE für die Tabelle in der Datenbank.

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)