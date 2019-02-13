---
title: Aktualisieren von Daten mit einem TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 546ca45ed48f9fc247bd5706005153f41cf206e5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926761"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualisieren von Daten mit einem TableAdapter

Nachdem die Daten im Dataset geändert und überprüft wurde, können Sie die aktualisierten Daten in einer Datenbank senden, durch den Aufruf der `Update` Methode eine [TableAdapter](../data-tools/create-and-configure-tableadapters.md). Die `Update` Methode eine einzelnen Datentabelle aktualisiert und führt den richtigen Befehl (INSERT, UPDATE oder DELETE) basierend auf den <xref:System.Data.DataRow.RowState%2A> der einzelnen Datenzeilen in der Tabelle. Wenn Sie ein Dataset verknüpfte Tabellen aufweist, generiert Visual Studio eine TableAdapterManager-Klasse, die Sie verwenden, um die Updates führen. Die TableAdapterManager-Klasse wird sichergestellt, dass Updates vorgenommen werden, in der richtigen Reihenfolge basierend auf den Fremdschlüssel-Einschränkungen, die in der Datenbank definiert sind. Wenn Sie datengebundene Steuerelemente verwenden, erstellt die Databinding-Architektur eine Membervariable der TableAdapterManager namens TableAdapterManager-Klasse.

> [!NOTE]
> Wenn Sie versuchen, eine Datenquelle mit dem Inhalt eines Datasets zu aktualisieren, können Sie Fehler abrufen. Um Fehler zu vermeiden, wird empfohlen, dass Sie den Code einfügen, die Aufrufe des Adapters `Update` Methode innerhalb einer `try` / `catch` Block.

 Das genaue Verfahren zum Aktualisieren einer Datenquelle kann je nach unternehmensanforderungen variieren, aber es enthält die folgenden Schritte aus:

1.  Aufrufen des Adapters `Update` -Methode in einer `try` / `catch` Block.

2.  Lokalisieren der fehlerhaften Datenzeile, falls eine Ausnahme abgefangen wird.

3.  Beheben Sie das Problem in der Zeile (programmgesteuert oder durch die Bereitstellung der ungültigen Zeile dem Benutzer zur Änderung angezeigt wird), und wiederholen Sie dann das Update (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Speichern von Daten in einer Datenbank

Rufen Sie die `Update` -Methode eines TableAdapter. Übergeben Sie den Namen der Datentabelle, die die Werte enthält, in die Datenbank geschrieben werden sollen.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Zum Aktualisieren einer Datenbank mit einem TableAdapter

-   Schließen Sie der TableAdapters`Update` -Methode in einer `try` / `catch` Block. Das folgende Beispiel zeigt, wie Sie den Inhalt des Aktualisieren der `Customers` in Tabelle `NorthwindDataSet` innerhalb einer `try` / `catch` Block.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)