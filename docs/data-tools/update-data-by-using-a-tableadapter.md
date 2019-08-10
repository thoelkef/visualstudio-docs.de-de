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
ms.openlocfilehash: 61ebcd6c833b55f0769365b89274e35136c914f9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925352"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualisieren von Daten mit einem TableAdapter

Nachdem die Daten im Dataset geändert und überprüft wurden, können Sie die aktualisierten Daten zurück an eine Datenbank senden, indem Sie die `Update` -Methode eines [TableAdapter](../data-tools/create-and-configure-tableadapters.md)aufrufen. Die `Update` -Methode aktualisiert eine einzelne Datentabelle und führt den korrekten Befehl (INSERT, Update oder DELETE) basierend auf der <xref:System.Data.DataRow.RowState%2A> der einzelnen Daten Zeilen in der Tabelle aus. Wenn ein Dataset verknüpfte Tabellen enthält, generiert Visual Studio eine TableAdapterManager-Klasse, die Sie für die Updates verwenden. Die TableAdapterManager-Klasse stellt sicher, dass Aktualisierungen in der richtigen Reihenfolge basierend auf den Foreign Key-Einschränkungen vorgenommen werden, die in der Datenbank definiert sind. Wenn Sie Daten gebundene Steuerelemente verwenden, erstellt die Datenbindung-Architektur eine Member-Variable der TableAdapterManager-Klasse namens TableAdapterManager.

> [!NOTE]
> Wenn Sie versuchen, eine Datenquelle mit dem Inhalt eines Datasets zu aktualisieren, können Sie Fehlermeldungen erhalten. Um Fehler zu vermeiden, empfiehlt es sich, den Code, der die `Update` -Methode des Adapters aufruft, in einen `try` / `catch` -Block einzufügen.

Die genaue Vorgehensweise zum Aktualisieren einer Datenquelle kann je nach Geschäftsanforderungen variieren, umfasst jedoch die folgenden Schritte:

1. Ruft die `Update` -Methode des Adapters in `try` einem / `catch` -Block auf.

2. Lokalisieren der fehlerhaften Datenzeile, falls eine Ausnahme abgefangen wird.

3. Beheben Sie das Problem in der Daten Zeile (Programm gesteuert, wenn dies möglich ist, oder indem Sie die ungültige Zeile dem Benutzer zur Änderung präsentieren), und wiederholen<xref:System.Data.DataRow.HasErrors%2A>Sie <xref:System.Data.DataTable.GetErrors%2A>dann das Update (,).

## <a name="save-data-to-a-database"></a>Speichern von Daten in einer Datenbank

Ruft die `Update` -Methode eines TableAdapter auf. Übergeben Sie den Namen der Datentabelle, die die Werte enthält, die in die Datenbank geschrieben werden sollen.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>So aktualisieren Sie eine Datenbank mit einem TableAdapter

- Schließen Sie die-`Update` Methode des TableAdapter in einen-Block ein. `try` / `catch` Im folgenden Beispiel wird gezeigt, wie Sie den `Customers` Inhalt der-Tabelle in `NorthwindDataSet` von einem `try` / `catch` -Block aus aktualisieren können.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)