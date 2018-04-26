---
title: 'Vorgehensweise: Aktivieren Sie Pluralisierung ein, und deaktivieren (O-R-Designer)'
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
ms.openlocfilehash: a8c477ac276ce0ff9c292dc42ba2f5f7d1e53dd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Vorgehensweise: Aktivieren Sie Pluralisierung ein, und deaktivieren (O/R-Designer)
Standardmäßig, wenn Sie Datenbankobjekte ziehen, deren Namen Endziffern s oder Datenreihen aus **Server-Explorer**/**Datenbank-Explorer** auf die [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), die Namen der generierten Entitätsklassen von plural in Singular geändert werden. Damit soll verdeutlicht werden, dass die instanziierte Entitätsklasse einem einzigen Datensatz zugeordnet ist. Wird dem [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] beispielsweise die Tabelle Customers hinzugefügt, erhält die Entitätsklasse den Namen Customer, da die Klasse die Daten eines einzigen Kunden enthält.

> [!NOTE]
>  Pluralisierung ist standardmäßig nur in der englischsprachigen Version von Visual Studio aktiviert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>So schalten Sie Pluralisierung ein und aus

1.  Klicken Sie im Menü **Extras** auf **Optionen**.

2.  In der **Optionen** Dialogfeld erweitern Sie **Datenbanktools**.

    > [!NOTE]
    >  Wählen Sie **alle Einstellungen anzeigen** Wenn die **Datenbanktools** Knoten ist nicht sichtbar.

3.  Klicken Sie auf **O/R-Designer**.

4.  Festlegen **Pluralisierung von Namen** auf **aktiviert** = **"false"** Festlegen der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , damit es Klassennamen nicht geändert wird.

5.  Legen Sie **Pluralisierung von Namen** auf **aktiviert** = **"true"** anzuwendende Pluralisierungsregeln auf die Klassennamen von Objekten hinzugefügt der [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)