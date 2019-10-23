---
title: Debuggingdateien/allgemeine Eigenschaften/Projektmappen-Eigenschaften Seiten
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 735432db485277e2265479e625f5e8acaa2cc2e3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738398"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten (Dialogfeld)
Auf dieser Eigenschaftenseite wird angegeben, wo der Debugger beim Debuggen der Projektmappe nach Quelldateien sucht.

 Zum Öffnen der Eigenschaftenseite **Quelldateien debuggen** klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die betreffende Projektmappe und wählen dann im Kontextmenü **Eigenschaften** aus. Erweitern Sie den Ordner **Allgemeine Eigenschaften**, und klicken Sie auf die Seite **Quelldateien debuggen**.

 **Verzeichnisse mit Quellcode** Enthält eine Liste der Verzeichnisse, in denen der Debugger beim Debuggen der Projekt Mappe nach Quelldateien sucht. Unterverzeichnisse der angegebenen Verzeichnissen werden ebenfalls durchsucht.

 **Diese Quelldateien nicht suchen** Geben Sie die Namen aller Dateien ein, die der Debugger nicht lesen soll. Wird eine dieser Dateien vom Debugger in einem der oben angegebenen Verzeichnisse gefunden, wird diese ignoriert. Wenn während des Debuggens das Dialogfeld **Quellcode suchen** angezeigt wird und Sie auf **Abbrechen** klicken, wird die gesuchte Datei dieser Liste hinzugefügt, sodass der Debugger nicht länger nach dieser Datei sucht.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)