---
title: Erweitern der Funktionalität eines TableAdapter | Microsoft-Dokumentation
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
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672360"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Erweitern der Funktionalität eines TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Funktionalität eines TableAdapters erweitern, indem Sie der partiellen Klassendatei von TableAdapter Code hinzufügen.

 Der Code, der einen TableAdapter definiert, wird erneut generiert, wenn Änderungen am TableAdapter im **DataSet-Designer**vorgenommen werden oder wenn die Konfiguration eines TableAdapters von einem Assistenten geändert wird. Um zu verhindern, dass Ihr Code während der erneuten Generierung eines TableAdapters gelöscht wird, fügen Sie der partiellen Klassendatei von TableAdapter Code hinzu.

 Partielle Klassen erlauben, dass Code für eine bestimmte Klasse auf mehrere physische Dateien aufgeteilt wird. Weitere Informationen finden Sie unter [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) oder [Partial (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

## <a name="locate-tableadapters-in-code"></a>Suchen von TableAdapters im Code
 Obwohl TableAdapters mit dem **DataSet-Designer**entworfen wurden, sind die generierten TableAdapter-Klassen keine geschposteten Klassen von <xref:System.Data.DataSet> . TableAdapters befinden sich in einem Namespace, der auf dem Namen des zugeordneten Datasets des TableAdapter basiert. Wenn die Anwendung z. b. ein DataSet `HRDataSet` mit dem Namen enthält, befinden sich die TableAdapters im- `HRDataSetTableAdapters` Namespace. (Die Benennungs Konvention folgt diesem Muster: *DataSetName*  +  `TableAdapters` ).

 Im folgenden Beispiel wird angenommen, dass sich ein TableAdapter namens `CustomersTableAdapter` in einem Projekt mit dem Namen befindet `NorthwindDataSet` .

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>So erstellen Sie eine partielle Klasse für einen TableAdapter

1. Fügen Sie dem Projekt eine neue Klasse hinzu, indem Sie im Menü **Projekt** auf**Klasse hinzufügen**klicken.

2. Geben Sie der Klassen den Namen `CustomersTableAdapterExtended`.

3. Wählen Sie **Hinzufügen**.

4. Ersetzen Sie den Code durch den korrekten Namespace und den Namen der partiellen Klasse für Ihr Projekt wie folgt:

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>Weitere Informationen
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
