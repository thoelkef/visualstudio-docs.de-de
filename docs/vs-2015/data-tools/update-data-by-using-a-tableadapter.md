---
title: Aktualisieren von Daten mit einem TableAdapter | Microsoft-Dokumentation
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
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 312bf75100d2b9b270b45776c5f7ded21ab6ac52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602331"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualisieren von Daten mit einem TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nachdem die Daten in Ihrem Dataset geändert und überprüft wurden, können Sie die aktualisierten Daten an eine Daten bankdatenbank zurücksenden, indem Sie die- `Update` Methode eines TableAdapter aufrufen. Die `Update` -Methode aktualisiert eine einzelne Datentabelle und führt den korrekten Befehl (INSERT, Update oder DELETE) basierend auf der <xref:System.Data.DataRow.RowState%2A> der einzelnen Daten Zeilen in der Tabelle aus. Wenn ein Dataset verknüpfte Tabellen enthält, generiert Visual Studio eine TableAdapterManager-Klasse, die Sie für die Updates verwenden. Die TableAdapterManager-Klasse stellt sicher, dass Aktualisierungen in der richtigen Reihenfolge basierend auf den Foreign Key-Einschränkungen vorgenommen werden, die in der Datenbank definiert sind. Wenn Sie Daten gebundene Steuerelemente verwenden, erstellt die Datenbindung-Architektur eine Member-Variable der TableAdapterManager-Klasse namens TableAdapterManager. Weitere Informationen finden Sie unter [Übersicht über hierarchische Updates](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).

> [!NOTE]
> Wenn Sie versuchen, eine Datenquelle mit dem Inhalt eines Datasets zu aktualisieren, können Sie Fehlermeldungen erhalten. Um Fehler zu vermeiden, wird empfohlen, dass Sie den Code, der die-Methode des Adapters aufruft, `Update` in einen- `try` / `catch` Block einfügen.

 Die genaue Vorgehensweise zum Aktualisieren einer Datenquelle kann je nach Geschäftsanforderungen variieren, umfasst jedoch die folgenden Schritte:

1. Ruft die-Methode des Adapters `Update` in einem- `try` / `catch` Block auf.

2. Lokalisieren der fehlerhaften Datenzeile, falls eine Ausnahme abgefangen wird. Weitere Informationen finden Sie unter Gewusst [wie: Suchen von Zeilen, die Fehler](https://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c)enthalten.

3. Beheben Sie das Problem in der Daten Zeile (Programm gesteuert, wenn dies möglich ist, oder indem Sie die ungültige Zeile dem Benutzer zur Änderung präsentieren), und wiederholen Sie dann das Update ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="savedata-to-a-database"></a>SaveData in einer Datenbank
 Ruft die- `Update` Methode eines TableAdapter auf. Übergeben Sie den Namen der Datentabelle, die die Werte enthält, die in die Datenbank geschrieben werden sollen.

#### <a name="to-update-a-database-by-using-a-tableadapter"></a>So aktualisieren Sie eine Datenbank mit einem TableAdapter

- Schließen Sie die-Methode des TableAdapter `Update` in einen- `try` / `catch` Block ein. Im folgenden Beispiel wird gezeigt, wie Sie den Inhalt der- `Customers` Tabelle in `NorthwindDataSet` von einem-Block aus aktualisieren können `try` / `catch` .

     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]

## <a name="see-also"></a>Weitere Informationen
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
