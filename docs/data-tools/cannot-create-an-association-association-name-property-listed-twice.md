---
title: Eine Zuordnung - Eigenschaft ist zweimal aufgelistet ist, kann nicht erstellt werden.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d508cc407087e481ff77e29956db7511bba81165
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916828"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Erstellen Sie eine Zuordnung kann nicht &lt;Zuordnungsname&gt; -Eigenschaft ist zweimal aufgelistet

Erstellen Sie eine Zuordnung kann nicht \<Association-Name >. Die gleiche Eigenschaft ist mehrmals aufgelistet: \<Eigenschaftennamen >.

Zuordnungen definiert sind vom ausgewählten **Zuordnungseigenschaften** in der **Zuordnungs-Editor** (Dialogfeld). Eigenschaften können für jede Klasse in der Zuordnung nur einmal aufgelistet werden.

Die Eigenschaft in der Meldung wird angezeigt, in der über- oder untergeordneten Klasse mehr als einmal **Zuordnungseigenschaften**.

## <a name="to-resolve-this-condition"></a>So lösen Sie dieses Problem

- Untersuchen Sie die Meldung, und notieren Sie die in der Meldung angegebene Eigenschaft.

- Klicken Sie auf **OK** auf das Meldungsfeld zu schließen.

- Überprüfen Sie die **Zuordnungseigenschaften** und entfernen Sie die doppelten Einträge.

- Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Vorgehensweise: Erstellen einer Assoziation zwischen LINQ to SQL-Klassen (O/R-Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)