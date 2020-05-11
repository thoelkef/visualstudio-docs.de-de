---
title: Auskommentieren von Code
description: In diesem Artikel wird die Verwendung von Kommentaren im Quellcode-Editor von Visual Studio für Mac beschrieben.
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 2966d8b89a2609d3fbfc2b6b4561288433641ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2020
ms.locfileid: "67693110"
---
# <a name="comments"></a>Kommentare

Beim Debuggen oder Experimentieren mit Code kann es nützlich sein, Codeblöcke vorübergehend oder langfristig zu kommentieren.

So kommentieren Sie einen kompletten Codeblock:

* Wählen Sie den Code aus und klicken Sie dann im Kontextmenü auf **Zeilenkommentar umschalten**.

oder

* Verwenden Sie die Schlüsselbindung `cmd + /` für den ausgewählten Code.

Diese Methoden können zum Kommentieren oder Auskommentieren von Codeabschnitten verwendet werden. In C#-Dateien können zusätzliche Zeilenkommentarebenen hinzugefügt werden, sodass Teile von Code kommentiert und auskommentiert werden können, während tatsächliche Kommentare beibehalten werden können:

![Kommentare mit mehreren Ebenen](media/source-editor-image8.png)

Kommentare sind zudem beim Dokumentieren von Code für die Interaktion zukünftiger Entwickler nützlich. Diese sind meistens mehrzeilige Kommentare, die folgendermaßen in der jeweiligen Sprache hinzugefügt werden:

**C#**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>Weitere Informationen

- [Auskommentieren von Code (Visual Studio unter Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)