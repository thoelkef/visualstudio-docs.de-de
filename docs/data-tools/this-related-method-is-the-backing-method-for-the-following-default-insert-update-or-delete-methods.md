---
title: Diese verknüpfte Methode ist die Sicherungsmethode für die folgenden standardmäßigen Methoden zum Einfügen, Aktualisieren oder Löschen.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc83bc78aace73cedf186b5ec925dce0a509b91d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565471"
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