---
title: "Debuggen von Quelle Dateien, allgemeine Eigenschaften Lösung Property Pages Dialog Box | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.options.FindSource
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
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: aa83025b15fe3773220a2b27394890318d60c850
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2018
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten (Dialogfeld)
Auf dieser Eigenschaftenseite wird angegeben, wo der Debugger beim Debuggen der Projektmappe nach Quelldateien sucht.  
  
 Für den Zugriff auf die **Quelldateien debuggen** auf der Seite mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer** , und wählen Sie **Eigenschaften** aus dem Kontextmenü. Erweitern Sie die **allgemeine Eigenschaften** Ordner, und klicken Sie auf die **Quelldateien debuggen** Seite.  
  
 **Verzeichnisse mit Quellcode**  
 Darin enthalten ist eine Liste der Verzeichnisse, in denen der Debugger beim Debuggen der Projektmappe nach Quelldateien sucht. Unterverzeichnisse der angegebenen Verzeichnissen werden ebenfalls durchsucht.  
  
 **Nach folgenden Quelldateien nicht suchen**  
 Geben Sie hier die Namen aller Quelldateien ein, die vom Debugger nicht gelesen werden sollen. Wird eine dieser Dateien vom Debugger in einem der oben angegebenen Verzeichnisse gefunden, wird diese ignoriert. Wenn die **Quellcode suchen** Dialogfeld hochgefahren wird, während Sie Debuggen, und Sie auf **"Abbrechen"**, die Datei, die Sie für die Suche wurden zu dieser Liste hinzugefügt, damit der Debugger nicht länger wird nach dieser Datei sucht.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)