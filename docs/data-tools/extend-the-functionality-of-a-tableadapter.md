---
title: Erweitern der Funktionalität eines TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a5b34bcb9c1532190f730e26c691289d489a2f3c
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50751075"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Erweitern der Funktionalität eines TableAdapter

Sie können die Funktionalität eines TableAdapter erweitern, indem partiellen Klassendatei für die TableAdapter Code hinzufügen.

Der Code, der einen TableAdapter definiert wird erneut generiert, wenn Änderungen, um den TableAdapter im vorgenommen werden der **Dataset-Designer**, oder wenn ein Assistent ändert die Konfiguration eines TableAdapter. Um zu verhindern, dass Ihr Code beim erneuten Generieren eines TableAdapter gelöscht wird, fügen Sie Code zur Datei für die TableAdapter partielle Klasse.

Partielle Klassen können Sie Code für eine bestimmte Klasse auf mehrere physische Dateien unterteilt werden. Weitere Informationen finden Sie unter [teilweise](/dotnet/visual-basic/language-reference/modifiers/partial) oder [Partial (Typ)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Suchen Sie TableAdapters im code

Während TableAdapters mit entworfen werden die **Dataset-Designer**, die TableAdapter-Klassen, die generiert werden, sind nicht geschachtelten Klassen von <xref:System.Data.DataSet>. TableAdapters befinden sich in einem Namespace, die basierend auf den Namen des zugeordneten Datasets des TableAdapter. Wenn Ihre Anwendung ein Dataset Namens enthält, z. B. `HRDataSet`, befindet sich die TableAdapters in die `HRDataSetTableAdapters` Namespace. (Die Benennungskonvention folgt diesem Muster: *DatasetName* + `TableAdapters`).

Im folgende Beispiel wird davon ausgegangen, einen TableAdapter namens `CustomersTableAdapter`befindet sich in einem Projekt mit `NorthwindDataSet`.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Um eine partielle Klasse für einen TableAdapter zu erstellen.

1.  Fügen Sie eine neue Klasse hinzu, indem Sie auf die **Projekt** Menü und auswählen **Klasse hinzufügen**.

2.  Nennen Sie die Klasse `CustomersTableAdapterExtended`.

3.  Wählen Sie **Hinzufügen** aus.

4.  Ersetzen Sie den Code mit den richtigen Namespace und den Namen der partiellen Klasse für das Projekt wie folgt:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)