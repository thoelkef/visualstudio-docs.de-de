---
title: 'Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 54b3376f9388116f179e2b09bcd136a37f3029f5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586444"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Vorgehensweise: Aktivieren/Deaktivieren der Pluralisierung (O/R-Designer)
Wenn Sie Datenbankobjekte mit Namen, die in s oder IES enden, von **Server-Explorer** oder **Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)ziehen, werden die Namen der generierten Entitäts Klassen standardmäßig von Plural in Singular geändert. Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist. Wenn Sie z. b. eine `Customers` Tabelle zum **O/R-Designer** hinzufügen, führt dies zu einer Entitäts Klasse mit dem Namen `Customer`, da die Klasse nur Daten für einen einzelnen Kunden enthält.

> [!NOTE]
> Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>So schalten Sie Pluralisierung ein und aus

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Erweitern Sie im Dialogfeld **Optionen** den Knoten **Datenbanktools**.

    > [!NOTE]
    > Wählen Sie **Alle Einstellungen anzeigen** aus, wenn der Knoten **Datenbanktools** nicht angezeigt wird.

3. Klicken Sie auf **O/R-Designer**.

4. Legen Sie die **Pluralisierung von Namen** auf **aktiviert** = **false** fest, um den **O/R-Designer** so festzulegen, dass er die Klassennamen nicht ändert.

5. Legen Sie die **Pluralisierung von Namen** auf **aktiviert** fest = **true** , um pluralisierungs Regeln auf die Klassennamen von Objekten anzuwenden, die dem **O/R-Designer**hinzugefügt wurden.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
