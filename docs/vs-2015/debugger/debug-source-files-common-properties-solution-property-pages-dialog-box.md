---
title: Debuggen von Quelle, allgemeine Eigenschaften, Lösung Eigenschaft Eigenschaftenseiten (Dialogfeld) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47fb2511e39153753a2c27483dd6ac96c26c9e83
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143031"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Auf dieser Eigenschaftenseite wird angegeben, wo der Debugger beim Debuggen der Projektmappe nach Quelldateien sucht.  
  
 Zum Öffnen der Eigenschaftenseite **Quelldateien debuggen** klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die betreffende Projektmappe und wählen dann im Kontextmenü **Eigenschaften** aus. Erweitern Sie den Ordner **Allgemeine Eigenschaften**, und klicken Sie auf die Seite **Quelldateien debuggen**.  
  
 **Verzeichnisse mit Quellcode**  
 Darin enthalten ist eine Liste der Verzeichnisse, in denen der Debugger beim Debuggen der Projektmappe nach Quelldateien sucht. Unterverzeichnisse der angegebenen Verzeichnissen werden ebenfalls durchsucht.  
  
 **Nach folgenden Quelldateien nicht suchen**  
 Geben Sie hier die Namen aller Quelldateien ein, die vom Debugger nicht gelesen werden sollen. Wird eine dieser Dateien vom Debugger in einem der oben angegebenen Verzeichnisse gefunden, wird diese ignoriert. Wenn während des Debuggens das Dialogfeld **Quellcode suchen** angezeigt wird und Sie auf **Abbrechen** klicken, wird die gesuchte Datei dieser Liste hinzugefügt, sodass der Debugger nicht länger nach dieser Datei sucht.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger Security (Debuggersicherheit)](../debugger/debugger-security.md)   
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
