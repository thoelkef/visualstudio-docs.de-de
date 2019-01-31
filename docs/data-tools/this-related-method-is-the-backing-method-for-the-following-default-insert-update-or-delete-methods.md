---
title: Diese verknüpfte Methode ist die Sicherungsmethode für die folgenden standardmäßigen Methoden zum Einfügen, Aktualisieren oder Löschen.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 4b478f041dcd94cff58f9bff8121e8d6e3b8acd3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069342"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Diese verknüpfte Methode ist die Sicherungsmethode für die folgenden standardmäßigen Methoden zum Einfügen, Aktualisieren oder Löschen.

Diese verknüpfte Methode ist die dahinter liegende Methode für die folgenden Standardgruppen `Insert`, `Update`, oder `Delete` Methoden. Wenn sie gelöscht wird, werden die entsprechenden Methoden ebenfalls gelöscht. Möchten Sie den Vorgang fortsetzen?

Die ausgewählte `DataContext` Methode dient als eines der derzeit die `Insert`, `Update`, oder `Delete` Methoden für eine der Entitätsklassen der **O/R Designer**. Löschen die Ursachen für die ausgewählte Methode die Entitätsklasse, die diese Methode verwendet wurde, wieder in den das Standardverhalten für die Laufzeit für die Aktionen einfügen, aktualisieren oder Löschen während einer Aktualisierung.

## <a name="selected-method-options"></a>Optionen für die ausgewählte Methode

- So löschen Sie die ausgewählte Methode, sodass die Entitätsklasse Laufzeitupdates, verwendet klicken Sie auf **Ja**.

   Die ausgewählte Methode wird gelöscht und alle Klassen, die diese Methode zum Überschreiben des Updateverhaltens verwendet hatten, greifen wieder auf das standardmäßige LINQ to SQL-Laufzeitverhalten zurück.

- Schließen Sie das Meldungsfeld, ohne die ausgewählte Methode unverändert ist, klicken Sie auf **keine**.

   Das Meldungsfeld wird geschlossen, und es werden keine Änderungen vorgenommen.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)