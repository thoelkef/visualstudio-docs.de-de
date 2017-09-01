---
title: Kommentare
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: cb44dc755721f6095c9a07ad3e6fec1f6849e149
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

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

``` cs
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

