---
title: Debuggen von Quelle, allgemeine Eigenschaften, Lösung Eigenschaft Eigenschaftenseiten (Dialogfeld) | Microsoft-Dokumentation
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
ms.openlocfilehash: 83bed0588a0959ab85906d949e1b0752396223ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852911"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten (Dialogfeld)
Auf dieser Eigenschaftenseite wird angegeben, wo der Debugger beim Debuggen der Projektmappe nach Quelldateien sucht.

 Zum Öffnen der Eigenschaftenseite **Quelldateien debuggen** klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die betreffende Projektmappe und wählen dann im Kontextmenü **Eigenschaften** aus. Erweitern Sie den Ordner **Allgemeine Eigenschaften**, und klicken Sie auf die Seite **Quelldateien debuggen**.

 **Verzeichnisse mit Quellcode** enthält eine Liste der Verzeichnisse, in dem der Debugger nach Quelldateien beim Debuggen der Projektmappe sucht. Unterverzeichnisse der angegebenen Verzeichnissen werden ebenfalls durchsucht.

 **Quelldateien nicht suchen** Geben Sie die Namen von Dateien, die Sie nicht, dass den Debugger zum lesen möchten. Wird eine dieser Dateien vom Debugger in einem der oben angegebenen Verzeichnisse gefunden, wird diese ignoriert. Wenn während des Debuggens das Dialogfeld **Quellcode suchen** angezeigt wird und Sie auf **Abbrechen** klicken, wird die gesuchte Datei dieser Liste hinzugefügt, sodass der Debugger nicht länger nach dieser Datei sucht.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)