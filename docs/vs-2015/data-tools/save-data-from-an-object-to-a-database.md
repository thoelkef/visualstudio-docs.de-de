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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6980ecc7676afd978f8dfd243ef8f383413ad83d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074882"
---
# <a name="save-data-from-an-object-to-a-database"></a>Speichern von Daten aus einem Objekt in einer Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Daten in Objekten in einer Datenbank speichern, indem Sie die Werte aus dem Objekt eines TableAdapters-DBDirect-Methoden übergeben (z. B. `TableAdapter.Insert`).
  
 Klicken Sie zum Speichern von Daten aus einer Auflistung von Objekten, durchlaufen Sie die Auflistung von Objekten (z. B. eine for-Next-Schleife), und senden Sie die Werte für jedes Objekt an die Datenbank mithilfe einer der TableAdapters-DBDirect-Methoden.  
  
 Standardmäßig werden die DBDirect-Methoden auf einem TableAdapter erstellt, die direkt in der Datenbank ausgeführt werden können. Diese Methoden können direkt aufgerufen werden und erfordern keine <xref:System.Data.DataSet> oder <xref:System.Data.DataTable> Objekte Änderungen abstimmen, um Updates in einer Datenbank zu senden.  
  
> [!NOTE]
>  Wenn Sie einen TableAdapter konfigurieren, muss die Hauptabfrage genügend Informationen für die DBDirect-Methoden, die erstellt werden, angeben. Z. B. wenn ein TableAdapter zum Abfragen von Daten aus einer Tabelle, die nicht über eine primäre Schlüsselspalte definiert verfügt konfiguriert ist, wird es nicht DBDirect-Methoden generiert.  
  
|TableAdapter-DBDirect-Methode|Beschreibung|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Fügt neue Datensätze in einer Datenbank und ermöglicht es Ihnen, einzelne Spaltenwerte als Methodenparameter übergeben.|  
|`TableAdapter.Update`|Aktualisiert vorhandene Datensätze in einer Datenbank. Die `Update` Methode übernimmt die Werte der ursprünglichen und neuen Spalte als Methodenparameter. Die ursprünglichen Werte werden verwendet, um den ursprünglichen Datensatz zu suchen, und die neuen Werte werden verwendet, um diesen Datensatz aktualisieren.<br /><br /> Die `TableAdapter.Update` Methode dient auch zum Abstimmen von Änderungen in einem Dataset zurück an die Datenbank mithilfe einer <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, oder ein Array von <xref:System.Data.DataRow>s als Methodenparameter.|  
|`TableAdapter.Delete`|Löscht den vorhandenen Datensätze aus der Datenbank, die basierend auf den ursprünglichen Spaltenwerte als Methodenparameter übergeben.|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>Um neue Datensätze aus einem Objekt in einer Datenbank zu speichern.  
  
- Erstellen Sie die Datensätze durch Übergeben der Werte, die `TableAdapter.Insert` Methode.  
  
     Das folgende Beispiel erstellt einen neuer Kundendatensatz in der `Customers` Tabelle durch Übergeben der Werte in der `currentCustomer` -Objekt an die `TableAdapter.Insert` Methode.  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Zum Aktualisieren vorhandener Datensätze aus einem Objekt in einer Datenbank  
  
- Ändern Sie die Datensätze durch Aufrufen der `TableAdapter.Update` -Methode, indem Sie die neuen Werte zur Aktualisierung des Datensatzes übergeben und in den ursprünglichen Werten den Datensatz gesucht.  
  
    > [!NOTE]
    >  Die ursprünglichen Werte beibehalten werden, um sie übergeben das Objekt muss die `Update` Methode. Dieses Beispiel verwendet die Eigenschaften mit einem `orig` Präfix, das die ursprünglichen Werte zu speichern.  
  
     Das folgende Beispiel aktualisiert einen vorhandenen Datensatz in die `Customers` Tabelle übergeben Sie die neuen und ursprünglichen Werte in der `Customer` -Objekt an die `TableAdapter.Update` Methode.  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>So löschen Sie vorhandene Datensätze aus einer Datenbank  
  
- Löschen Sie die Datensätze durch Aufrufen der `TableAdapter.Delete` -Methode und übergeben die ursprünglichen Werte den Datensatz gesucht.  
  
    > [!NOTE]
    >  Die ursprünglichen Werte beibehalten werden, um sie übergeben das Objekt muss die `Delete` Methode. Dieses Beispiel verwendet die Eigenschaften mit einem `orig` Präfix, das die ursprünglichen Werte zu speichern.  
  
     Das folgende Beispiel löscht einen Datensatz aus der `Customers` Tabelle übergeben Sie die ursprünglichen Werte in der `Customer` -Objekt an die `TableAdapter.Delete` Methode.  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Sie benötigen die Berechtigung zum Ausführen des ausgewählten INSERT-, Update- oder DELETE für die Tabelle in der Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
