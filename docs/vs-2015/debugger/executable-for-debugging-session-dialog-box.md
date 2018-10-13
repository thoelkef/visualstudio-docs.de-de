---
title: Ausführbare Datei für das Debuggen (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d1279ba5b3ed79c4115143a72e4543bbd6c123d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189825"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Ausführbare Datei für die Debugsitzung (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Dialogfeld wird angezeigt, wenn Sie eine DLL debuggen, für die keine ausführbare Datei festgelegt wurde. In Visual Studio können DLLs nicht direkt gestartet werden. Stattdessen wird die angegebene ausführbare Datei ausgeführt. Sie können die DLL debuggen, wenn diese durch die ausführbare Datei aufgerufen wird.  
  
 **Name der ausführbaren Datei**  
 Geben Sie den Pfad zu einer ausführbaren Datei ein, mit der die zu debuggende DLL aufgerufen wird.  
  
 **URL, in dem das Projekt zugegriffen kann (nur ATL-Server werden)**  
 Wenn Sie eine ATL-Server-DLL debuggen, geben Sie die URL ein, unter der sich das Projekt befindet.  
  
 Nach der Eingabe werden diese Einstellungen in den Eigenschaftenseiten des Projekts gespeichert, sodass Sie diese bei späteren Debugsitzungen nicht erneut eingeben müssen. Wenn Sie diese Einstellungen ändern möchten, können Sie die Eigenschaftenseiten öffnen und die Werte ändern. Weitere Informationen zum Angeben einer ausführbaren Datei für die Debugsitzung finden Sie unter [Debuggen von DLLs](../debugger/how-to-debug-native-dlls.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)



