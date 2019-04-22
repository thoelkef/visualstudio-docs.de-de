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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 585dfa357082fbb46794ab5f6dcc7b0e141fc9b7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653750"
---
# <a name="update-data-by-using-a-tableadapter"></a>Aktualisieren von Daten mit einem TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nachdem die Daten im Dataset geändert und überprüft wurde, können Sie die aktualisierten Daten senden, an einen Databaseby-Aufruf die `Update` -Methode eines TableAdapter. Die `Update` Methode eine einzelnen Datentabelle aktualisiert und führt den richtigen Befehl (INSERT, UPDATE oder DELETE) basierend auf den <xref:System.Data.DataRow.RowState%2A> der einzelnen Datenzeilen in der Tabelle. Wenn Sie ein Dataset verknüpfte Tabellen aufweist, generiert Visual Studio eine TableAdapterManager-Klasse, die Sie verwenden, um die Updates führen. Die TableAdapterManager-Klasse wird sichergestellt, dass Updates vorgenommen werden, in der richtigen Reihenfolge basierend auf den Fremdschlüssel-Einschränkungen, die in der Datenbank definiert sind. Wenn Sie datengebundene Steuerelemente verwenden, erstellt die Databinding-Architektur eine Membervariable der TableAdapterManager namens TableAdapterManager-Klasse. Weitere Informationen finden Sie unter [Übersicht über hierarchische Update](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Wenn Sie versuchen, eine Datenquelle mit dem Inhalt eines Datasets zu aktualisieren, können Sie Fehler abrufen. Um Fehler zu vermeiden, es wird empfohlen Thatyou platzieren Sie den Code, der Aufrufe des Adapters `Update` Methode innerhalb einer `try` / `catch` Block.  
  
 Das genaue Verfahren zum Aktualisieren einer Datenquelle kann je nach unternehmensanforderungen variieren, aber es enthält die folgenden Schritte aus:  
  
1.  Aufrufen des Adapters `Update` -Methode in einer `try` / `catch` Block.  
  
2.  Lokalisieren der fehlerhaften Datenzeile, falls eine Ausnahme abgefangen wird. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen von Zeilen mit Fehlern](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Beheben Sie das Problem in der Zeile (programmgesteuert oder durch die Bereitstellung der ungültigen Zeile dem Benutzer zur Änderung angezeigt wird), und wiederholen Sie dann das Update (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).  
  
## <a name="savedata-to-a-database"></a>SaveData in einer Datenbank  
 Rufen Sie die `Update` -Methode eines TableAdapter. Übergeben Sie den Namen der Datentabelle, die die Werte enthält, in die Datenbank geschrieben werden sollen.  
  
#### <a name="to-update-a-database-by-using-a-tableadapter"></a>Zum Aktualisieren einer Datenbank mit einem TableAdapter  
  
-   Schließen Sie der TableAdapters`Update` -Methode in einer `try` / `catch` Block. Das folgende Beispiel zeigt, wie Sie den Inhalt des Aktualisieren der `Customers` in Tabelle `NorthwindDataSet` innerhalb einer `try` / `catch` Block.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
