---
title: 'Gewusst wie: Aktivieren/Deaktivieren der Pluralisierung (O / R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0a2d2e44efc284c38cfc450833839776effb9936
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089382"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Gewusst wie: Aktivieren/Deaktivieren der Pluralisierung (O/R Designer)
In der Standardeinstellung beim Ziehen Datenbankobjekte, deren Namen auf s oder ies enden, aus **Server-Explorer** oder **Datenbank-Explorer** auf die [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), Namen der generierten Entitätsklassen werden von der plural-in einzelne geändert. Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist. Beispielsweise durch Hinzufügen einer `Customers` Tabelle, auf die **O/R Designer** führt zu einer Entitätsklasse, die mit dem Namen `Customer` , da die Klasse die Daten für nur einen einzelnen Kunden enthält.

> [!NOTE]
>  Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>So schalten Sie Pluralisierung ein und aus

1.  Klicken Sie im Menü **Extras** auf **Optionen**.

2.  In der **Optionen** Dialogfeld erweitern Sie **Datenbanktools**.

    > [!NOTE]
    >  Wählen Sie **alle Einstellungen anzeigen** Wenn die **Datenbanktools** Knoten ist nicht sichtbar.

3.  Klicken Sie auf **O/R-Designer**.

4.  Legen Sie **Pluralisierung von Namen** zu **aktiviert** = **"false"** Festlegen der **O/R Designer** , damit es Klassennamen nicht geändert wird .

5.  Legen Sie **Pluralisierung von Namen** zu **aktiviert** = **"true"** anzuwendende Pluralisierungsregeln auf die Klassennamen von Objekten, die hinzugefügt, die **O/R Designer**.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)