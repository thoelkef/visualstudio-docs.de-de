---
title: Ausführbare Datei für das Debuggen (Dialogfeld) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d6bc004ac9d450e0f5ea358d16bb25ab6cabecf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018750"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Ausführbare Datei für die Debugsitzung (Dialogfeld)

Dieses Dialogfeld wird angezeigt, wenn Sie eine DLL debuggen, für die keine ausführbare Datei festgelegt wurde. Eine DLL-Datei kann nicht von Visual Studio direkt gestartet werden. Stattdessen startet Visual Studio die angegebene ausführbare Datei. Sie können die DLL debuggen, wenn sie die ausführbare Datei aufgerufen wird.  
  
 **Name der ausführbaren Datei**  
 Geben Sie den Pfad zu einer ausführbaren Datei ein, mit der die zu debuggende DLL aufgerufen wird.  
  
 **URL, von der aus auf das Projekt zugegriffen werden kann (nur ATL-Server)**  
 Wenn Sie eine ATL-Server-DLL debuggen, geben Sie die URL ein, unter der sich das Projekt befindet.  
  
 Nach der Eingabe werden diese Einstellungen im Projekt-Eigenschaftenseiten gespeichert, sodass Sie nicht bei späteren Debugsitzungen erneut eingeben müssen. Wenn Sie diese Einstellungen ändern möchten, können Sie die Eigenschaftenseiten öffnen und die Werte ändern. Weitere Informationen zum Angeben einer ausführbaren Datei für die Debugsitzung finden Sie unter [Debuggen von DLLs](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>Siehe auch

 [Debuggen in Visual Studio](../debugger/index.md)  
 [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)