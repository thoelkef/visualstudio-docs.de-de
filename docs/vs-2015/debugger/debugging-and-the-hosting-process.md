---
title: Debuggen und der Hostprozess | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5cc008f12f4312df2d63f019a0d33a7b727e5ae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511497"
---
# <a name="debugging-and-the-hosting-process"></a>Debuggen und der Hostprozess
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Debuggen und der Hostprozess](https://docs.microsoft.com/visualstudio/debugger/debugging-and-the-hosting-process).  
  
Der Visual Studio-Hostprozess verbessert die Debugleistung und ermöglicht neue Debuggerfeatures, z. B. das Debuggen von teilweise vertrauenswürdigen Anwendungen und die Ausdrucksauswertung zur Entwurfszeit. Falls erforderlich, können Sie den Hostprozess deaktivieren. Weitere Informationen finden Sie unter [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md). In den folgenden Abschnitten werden einige der Unterschiede beschrieben, die zwischen dem Debuggen mit und ohne den Hostprozess bestehen.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Debuggen teilweise vertrauenswürdiger Anwendungen und ClickOnce-Sicherheit  
 Zum Debuggen teilweise vertrauenswürdiger Anwendungen ist der Hostprozess erforderlich. Wenn Sie den Hostprozess deaktivieren, ist das Debuggen teilweise vertrauenswürdiger Anwendungen nicht möglich, selbst wenn auf der **Sicherheitsseite** der **Projekteigenschaften**die Sicherheit bei teilweiser Vertrauenswürdigkeit aktiviert wurde. Weitere Informationen finden Sie unter [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md) und [How to: Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Ausdrucksauswertung zur Entwurfszeit  
 Bei der Ausdrucksauswertung zur Entwurfszeit wird stets auf den Hostprozess zugegriffen. Wird der Hostprozess in den **Projekteigenschaften** deaktiviert, so wird damit auch die Ausdrucksauswertung zur Entwurfszeit für Klassenbibliotheksprojekte deaktiviert. Für die anderen Projekttypen steht die Ausdrucksauswertung zur Entwurfszeit weiterhin zur Verfügung. Visual Studio startet stattdessen die eigentliche ausführbare Datei und verwendet diese zur Evaluierung während der Entwurfszeit, ohne auf den Hostprozess zuzugreifen. Dies führt möglicherweise zu abweichenden Ergebnissen.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Unterschiede bezüglich "AppDomain.CurrentDomain.FriendlyName"  
 Abhängig davon, ob der Hostprozess aktiviert ist oder nicht, liefert`AppDomain.CurrentDomain.FriendlyName` unterschiedliche Ergebnisse. Wenn Sie `AppDomain.CurrentDomain.FriendlyName` bei aktiviertem Hostprozess aufrufen, wird *app_name*`.vhost.exe`zurückgegeben. Wenn der Aufruf bei deaktiviertem Hostprozess erfolgt, wird *app_name*`.exe`zurückgegeben.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Unterschiede bezüglich "Assembly.GetCallingAssembly().FullName"  
 Abhängig davon, ob der Hostprozess aktiviert ist oder nicht, liefert`Assembly.GetCallingAssembly().FullName` unterschiedliche Ergebnisse. Wenn Sie `Assembly.GetCallingAssembly().FullName` bei aktiviertem Hostprozess aufrufen, wird `mscorlib`zurückgegeben. Wird `Assembly.GetCallingAssembly().FullName` bei deaktiviertem Hostprozess aufgerufen, wird der Anwendungsname zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Hostprozess („vshost.exe“)](../ide/hosting-process-vshost-exe.md)   
 [Vorgehensweise: Debuggen eine teilweise vertrauenswürdigen Anwendung](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Gewusst wie: Deaktivieren des Hostprozesses](../ide/how-to-disable-the-hosting-process.md)



