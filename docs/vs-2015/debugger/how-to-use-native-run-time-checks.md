---
title: 'Vorgehensweise: Verwenden von systemeigenen Laufzeitprüfungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e90af82b5f3d7cd88d3b8488b0ebd9a4359b566f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511337"
---
# <a name="how-to-use-native-run-time-checks"></a>Gewusst wie: Verwenden von systemeigenen Laufzeitprüfungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: verwenden systemeigene Laufzeitüberprüfungen](https://docs.microsoft.com/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
In Visual C++ können Sie native [Runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b) häufige Laufzeitfehler abfangen:  
  
-   Beschädigung des Stapelzeigers  
  
-   Überläufe lokaler Arrays  
  
-   Beschädigung des Stapels  
  
-   Abhängigkeiten von nicht initialisierten lokalen Variablen  
  
-   Datenverlust nach einer Zuordnung zu einer kürzeren Variablen  
  
 Wenn Sie **/RTC** mit einem optimierten (**/O**) Build verwenden, wird ein Compilerfehler ausgelöst. Wenn Sie in einem optimierten Build ein `runtime_checks` -Pragma verwenden, hat das Pragma keine Auswirkungen.  
  
 Wenn Sie ein Programm mit aktivierten Laufzeitüberprüfungen debuggen, wird das Programm beim Auftreten eines Laufzeitfehlers standardmäßig unterbrochen und wechselt in den Debugger. Sie können dieses Standardverhalten für jede Laufzeitüberprüfung ändern. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 In den folgenden Prozeduren wird beschrieben, wie Sie in einem Debugbuild systemeigene Laufzeitüberprüfungen aktivieren und das Verhalten systemeigener Laufzeitüberprüfungen ändern.  
  
 Weitere Themen in diesem Abschnitt enthalten Informationen zu folgenden Vorgängen:  
  
-   [Anpassen von Laufzeitüberprüfungen mit der C-Laufzeitbibliothek](../debugger/native-run-time-checks-customization.md)  
  
-   [Verwenden von Laufzeitüberprüfungen ohne die C-Laufzeitbibliothek](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>So aktivieren Sie systemeigene Laufzeitfehlerüberprüfungen in einem Debugbuild  
  
-   Verwenden Sie die Option **/RTC** , und stellen Sie eine Verknüpfung zu der Debugversion einer C-Laufzeitbibliothek (z. B. /MDd) her.  
  
### <a name="to-modify-native-run-time-check-behavior"></a>So ändern Sie das Verhalten von systemeigenen Laufzeitfehlerüberprüfungen  
  
-   Verwenden Sie das `runtime_checks` -Pragma.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [Laufzeitfehlerüberprüfung](http://msdn.microsoft.com/library/c965dd01-57ad-4a3c-b1d6-5aa04f920501)





