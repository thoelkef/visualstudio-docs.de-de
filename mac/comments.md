---
title: Kommentare
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 0d49896a3c265dfdc5a25c46e80de498adfffb07
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
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
