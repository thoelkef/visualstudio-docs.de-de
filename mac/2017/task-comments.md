---
title: Aufgabenkommentare
description: Hinzufügen von Aufgabenkommentaren zum Code
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62987063"
---
# <a name="task-comments"></a>Aufgabenkommentare

Beim Schreiben von Code ist es üblich, unerledigten oder fragwürdigen Code explizit zu kommentieren oder schnelle Problemumgehungen mit Warnungen zu erstellen. Die Standardsignaltoken von Visual Studio für Mac sind TODO, HACK, FIXME und UNDONE. Personalisierte Token können unter **Visual Studio > Einstellungen > Umgebung > Aufgaben** definiert werden, wie in der folgenden Abbildung dargestellt:

![Aufgabenliste unter Einstellungen](media/source-editor-image10.png)

Um einen neuen Aufgabenkommentar hinzuzufügen, fügen Sie einen Kommentar ein, der das Aufgabenschlüsselwort enthält. Beispiel:

```csharp
//TODO: Finish this for all properties.
```

In Visual Studio für Mac werden diese Markierungen hervorgehoben, indem sie im Pad **Aufgabenliste** kenntlich gemacht werden, das durch Navigieren zu **Ansicht > Pads > Aufgabe** angezeigt werden kann:

![Bereich „Aufgabenliste“](media/source-editor-image11.png)

## <a name="see-also"></a>Siehe auch

- [Verwenden der Aufgabenliste (Visual Studio unter Windows)](/visualstudio/ide/using-the-task-list)