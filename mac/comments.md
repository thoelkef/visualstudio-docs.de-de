---
title: Auskommentieren von Code
description: In diesem Artikel wird die Verwendung von Kommentaren im Quellcode-Editor von Visual Studio für Mac beschrieben.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 1f792e5ba670854e4a3a9ce703212d18c16e5512
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295656"
---
# <a name="comments"></a>Kommentare

Beim Debuggen oder Experimentieren mit Code kann es nützlich sein, Codeblöcke vorübergehend oder langfristig zu kommentieren.

So kommentieren Sie einen kompletten Codeblock:

* Wählen Sie den Code aus und klicken Sie dann im Kontextmenü auf **Zeilenkommentar umschalten**.

ODER

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

## <a name="see-also"></a>Siehe auch

- [Auskommentieren von Code (Visual Studio unter Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)