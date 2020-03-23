---
title: Importelemente anzeigen
description: Verwenden Sie die Option „Importelemente anzeigen“, um IntelliSense in Visual Studio für Mac zu erweitern.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "75439103"
---
# <a name="show-import-items"></a>Importelemente anzeigen

Visual Studio für Mac kann alle verfügbaren Typen, auch wenn sie nicht in Ihr Projekt importiert wurden, in Ihrer IntelliSense-Vervollständigungsliste anzeigen. Wenn Sie ein Element auswählen, das nicht importiert wird, wird die richtige `using`-Anweisung zu Ihrer Quelldatei hinzugefügt.

![Importelemente anzeigen – Übersicht](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Vorgehensweise zum Aktivieren

Um dieses Feature zu aktivieren, öffnen Sie **Einstellungen** über **Visual Studio** > **Voreinstellungen** und navigieren Sie zu **Text-Editor** > **IntelliSense**. Aktivieren Sie das Kontrollkästchen **Importelemente anzeigen**, um zusätzliche Elemente in IntelliSense zu aktivieren.

![Importelemente anzeigen – Option](media/show-import-items.png)

## <a name="usage"></a>Verwendung

Sobald Sie **Importelemente anzeigen** aktivieren, gestaltet sich der Prozess der Verwendung des Features zum Importieren eines Elements ähnlich wie bei normalen Aktionen innerhalb von IntelliSense. Während Sie den Code eingeben, wird die Vervollständigungsliste mit gültigen Elementen gefüllt. Dazu gehören auch Elemente, die noch nicht importiert wurden. Die nicht importierten Elemente zeigen ihren vollständigen Namespace rechts neben dem Element an, sodass Sie sehen können, welche Importe Sie in Ihr Projekt pullen.

![Importelemente anzeigen – Liste](media/show-import-items-list.png)

In der IntelliSense-Liste werden Namespaces neben den Membern angezeigt, auf die derzeit nicht durch eine `using`-Anweisung verwiesen wird. Wenn Sie eines dieser Elemente aus der Liste auswählen, wird das Member zu Ihrem Code hinzugefügt _und_ die `using`-Anweisung wird am Anfang der Datei hinzugefügt. Member von Typen, auf die bereits im Code verwiesen wird, zeigen ihren Namespace in IntelliSense nicht an.

## <a name="see-also"></a>Weitere Informationen

- [Schnellaktionen (Visual Studio unter Windows)](/visualstudio/ide/quick-actions)
- [Umgestalten von Code (Visual Studio unter Windows)](/visualstudio/ide/refactoring-in-visual-studio)
