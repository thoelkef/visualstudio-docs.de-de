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
ms.openlocfilehash: 11c5c7d3c8078aa420074e9e32bb132489b169c8
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252944"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Diese verknüpfte Methode ist die Sicherungsmethode für die folgenden standardmäßigen Methoden zum Einfügen, Aktualisieren oder Löschen.

Diese verwandte Methode ist die Unterstützungs Methode für die folgenden Standard `Insert`- `Update`,- `Delete` oder-Methoden. Wenn sie gelöscht wird, werden die entsprechenden Methoden ebenfalls gelöscht. Möchten Sie den Vorgang fortsetzen?

Die ausgewählte `DataContext` Methode wird derzeit als `Insert`eine der Methoden, `Update`oder `Delete` für eine der Entitäts Klassen im **O/R-Designer**verwendet. Das Löschen der ausgewählten Methode bewirkt, dass die Entitäts Klasse, die diese Methode verwendet hat, zum standardmäßigen Laufzeitverhalten für das Einfügen, aktualisieren oder löschen während eines Updates zurückkehrt.

## <a name="selected-method-options"></a>Optionen für ausgewählte Methoden

- Um die ausgewählte Methode zu löschen, sodass die Entitäts Klasse Lauf Zeit Updates verwendet, klicken Sie auf **Ja**.

   Die ausgewählte Methode wird gelöscht, und alle Klassen, die diese Methode zum Überschreiben des Aktualisierungs Verhaltens verwendet haben, werden auf die standardmäßige LINQ to SQL Laufzeitverhalten zurückgesetzt.

- Um das Meldungs Feld zu schließen und die ausgewählte Methode unverändert zu lassen, klicken Sie auf **Nein**.

   Das Meldungsfeld wird geschlossen, und es werden keine Änderungen vorgenommen.

## <a name="see-also"></a>Siehe auch

- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)