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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e92b820b04913733095645d21ad682bff40acd84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648494"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Erweitern der Funktionalität eines TableAdapter

Sie können die Funktionalität eines TableAdapters erweitern, indem Sie der partiellen Klassendatei von TableAdapter Code hinzufügen.

Der Code, der einen TableAdapter definiert, wird erneut generiert, wenn Änderungen am TableAdapter im **DataSet-Designer**vorgenommen werden oder wenn die Konfiguration eines TableAdapters von einem Assistenten geändert wird. Um zu verhindern, dass Ihr Code während der erneuten Generierung eines TableAdapters gelöscht wird, fügen Sie der partiellen Klassendatei von TableAdapter Code hinzu.

Partielle Klassen erlauben, dass Code für eine bestimmte Klasse auf mehrere physische Dateien aufgeteilt wird. Weitere Informationen finden Sie unter [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) oder [Partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Suchen von TableAdapters im Code

Obwohl TableAdapters mit dem **DataSet-Designer**entworfen wurden, sind die generierten TableAdapter-Klassen keine geschposteten Klassen von <xref:System.Data.DataSet>. TableAdapters befinden sich in einem Namespace, der auf dem Namen des zugeordneten Datasets des TableAdapter basiert. Wenn Ihre Anwendung z. b. ein DataSet mit dem Namen `HRDataSet` enthält, befinden sich die TableAdapters im `HRDataSetTableAdapters`-Namespace. (Die Benennungskonvention folgt diesem Muster: *DatasetName* + `TableAdapters`).

Im folgenden Beispiel wird davon ausgegangen, dass ein TableAdapter mit dem Namen `CustomersTableAdapter`is in einem Projekt mit `NorthwindDataSet` ist.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>So erstellen Sie eine partielle Klasse für einen TableAdapter

1. Fügen Sie dem Projekt eine neue Klasse hinzu, indem Sie im Menü **Projekt** auf **Klasse hinzufügen**klicken.

2. Nennen Sie die Klasse `CustomersTableAdapterExtended`.

3. Wählen Sie **Hinzufügen** aus.

4. Ersetzen Sie den Code durch den korrekten Namespace und den Namen der partiellen Klasse für Ihr Projekt wie folgt:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)