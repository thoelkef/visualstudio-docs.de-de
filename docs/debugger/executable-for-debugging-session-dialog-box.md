---
title: Ausführbare Datei für die Sitzung (Dialogfeld) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98cee61b9a43e031daf468555f31349d10023fcc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473458"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Ausführbare Datei für die Debugsitzung (Dialogfeld)
Dieses Dialogfeld wird angezeigt, wenn Sie eine DLL debuggen, für die keine ausführbare Datei festgelegt wurde. In Visual Studio können DLLs nicht direkt gestartet werden. Stattdessen wird die angegebene ausführbare Datei ausgeführt. Sie können die DLL debuggen, wenn diese durch die ausführbare Datei aufgerufen wird.  
  
 **Name der ausführbaren Datei**  
 Geben Sie den Pfad zu einer ausführbaren Datei ein, mit der die zu debuggende DLL aufgerufen wird.  
  
 **URL, in dem das Projekt zugegriffen kann (nur ATL-Server werden)**  
 Wenn Sie eine ATL-Server-DLL debuggen, geben Sie die URL ein, unter der sich das Projekt befindet.  
  
 Nach der Eingabe werden diese Einstellungen in den Eigenschaftenseiten des Projekts gespeichert, sodass Sie diese bei späteren Debugsitzungen nicht erneut eingeben müssen. Wenn Sie diese Einstellungen ändern möchten, können Sie die Eigenschaftenseiten öffnen und die Werte ändern. Weitere Informationen zum Angeben einer ausführbaren Datei für die Debugsitzung finden Sie unter [Debuggen von DLLs](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md)  
 [Debugger – Featuretour](../debugger/debugger-feature-tour.md)