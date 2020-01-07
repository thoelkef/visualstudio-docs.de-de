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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ffb5139e148fba6facd1d437d4f7977d8d7e0b28
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586080"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualisieren von Daten mit einem TableAdapter

Nachdem die Daten im Dataset geändert und überprüft wurden, können Sie die aktualisierten Daten zurück an eine Datenbank senden, indem Sie die `Update`-Methode eines [TableAdapter](../data-tools/create-and-configure-tableadapters.md)aufrufen. Die `Update`-Methode aktualisiert eine einzelne Datentabelle und führt den korrekten Befehl (INSERT, Update oder DELETE) basierend auf der <xref:System.Data.DataRow.RowState%2A> jeder Daten Zeile in der Tabelle aus. Wenn ein Dataset verknüpfte Tabellen enthält, generiert Visual Studio eine TableAdapterManager-Klasse, die Sie für die Updates verwenden. Die TableAdapterManager-Klasse stellt sicher, dass Aktualisierungen in der richtigen Reihenfolge basierend auf den Foreign Key-Einschränkungen vorgenommen werden, die in der Datenbank definiert sind. Wenn Sie Daten gebundene Steuerelemente verwenden, erstellt die Datenbindung-Architektur eine Member-Variable der TableAdapterManager-Klasse namens TableAdapterManager.

> [!NOTE]
> Wenn Sie versuchen, eine Datenquelle mit dem Inhalt eines Datasets zu aktualisieren, können Sie Fehlermeldungen erhalten. Um Fehler zu vermeiden, empfiehlt es sich, den Code, der die `Update` Methode des Adapters aufruft, in einem `try`/`catch` Block zu platzieren.

Die genaue Vorgehensweise zum Aktualisieren einer Datenquelle kann je nach Geschäftsanforderungen variieren, umfasst jedoch die folgenden Schritte:

1. Ruft die `Update` Methode des Adapters in einer `try`/`catch` Blocks auf.

2. Lokalisieren der fehlerhaften Datenzeile, falls eine Ausnahme abgefangen wird.

3. Beheben Sie das Problem in der Daten Zeile (Programm gesteuert, wenn dies möglich ist, oder indem Sie die ungültige Zeile dem Benutzer zur Änderung präsentieren), und wiederholen Sie dann das Update (<xref:System.Data.DataRow.HasErrors%2A><xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Speichern von Daten in einer Datenbank

Ruft die `Update`-Methode eines TableAdapter auf. Übergeben Sie den Namen der Datentabelle, die die Werte enthält, die in die Datenbank geschrieben werden sollen.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>So aktualisieren Sie eine Datenbank mit einem TableAdapter

- Schließen Sie die`Update`-Methode des TableAdapter in einem `try`/`catch` Blocks ein. Im folgenden Beispiel wird gezeigt, wie der Inhalt der `Customers` Tabelle in `NorthwindDataSet` innerhalb eines `try`/`catch` Blocks aktualisiert wird.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
