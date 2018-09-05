---
title: Aufgabenkommentare
description: Hinzufügen von Aufgabenkommentaren zum Code
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 44d82becfbf3a16ccd2158ac05e171e8530cd721
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224195"
---
# <a name="task-comments"></a>Aufgabenkommentare

Beim Schreiben von Code ist es üblich, unerledigten oder fragwürdigen Code explizit zu kommentieren oder schnelle Problemumgehungen mit Warnungen zu erstellen. Die Standardsignaltoken von Visual Studio für Mac sind TODO, HACK, FIXME und UNDONE. Personalisierte Token können unter **Visual Studio > Voreinstellungen... > Umgebung > Aufgaben** definiert werden, wie in der folgenden Abbildung dargestellt:

 ![Aufgabenliste unter Einstellungen](media/source-editor-image10.png)

Um einen neuen Aufgabenkommentar hinzuzufügen, fügen Sie einen Kommentar ein, der das Aufgabenschlüsselwort enthält. Zum Beispiel:

```csharp
//TODO: Finish this for all properties.
```

In Visual Studio für Mac werden diese Markierungen hervorgehoben, indem sie im Bereich „Aufgabenliste“ kenntlich gemacht werden. Die Liste können Sie unter **Ansicht > Bereiche > Aufgabe** aufrufen:

![Bereich „Aufgabenliste“](media/source-editor-image11.png)