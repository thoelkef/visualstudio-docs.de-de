---
title: Eine Zuordnung kann nicht erstellt werden – Eigenschaft ist zweimal aufgelistet
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: acc2a34f8980d748df45ad8437e308c889170aba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648745"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Die Zuordnung &lt;Zuordnungsname&gt; kann nicht erstellt werden – Eigenschaft ist zweimal aufgelistet

Die Zuordnung \<Zuordnungsname> kann nicht erstellt werden. Die folgende Eigenschaft ist mehrmals aufgelistet: \<Eigenschaftenname>.

Zuordnungen werden im Dialogfeld **Zuordnungs-Editor** von den ausgewählten **Zuordnungseigenschaften** definiert. Eigenschaften können für jede Klasse in der Zuordnung nur einmal aufgelistet werden.

Die Eigenschaft in der Meldung wird in den **Zuordnungseigenschaften** der über- oder untergeordneten Klasse mehrmals aufgeführt.

## <a name="to-resolve-this-condition"></a>So lösen Sie dieses Problem

- Untersuchen Sie die Meldung, und notieren Sie die in der Meldung angegebene Eigenschaft.

- Klicken Sie auf **OK**, um das Meldungsfeld zu schließen.

- Überprüfen Sie die **Zuordnungseigenschaften**, und entfernen Sie die doppelten Einträge.

- Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Gewusst wie: Erstellen einer Zuordnung zwischen LINQ to SQL Klassen (O/R-Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)