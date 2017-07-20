---
title: Hostprozess (vshost.exe) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 96cd56eaeea20b2b0defcb60a188c9e13c19ec6a
ms.contentlocale: de-de
ms.lasthandoff: 05/26/2017

---
# Hostprozess (vshost.exe)
<a id="hosting-process-vshostexe" class="xliff"></a>
Der Visual Studio-Hostprozess verbessert die Debugleistung und ermöglicht das Debuggen von teilweise vertrauenswürdigen Anwendungen und die Ausdrucksauswertung zur Entwurfszeit. Die Hostprozessdateien enthalten vshost im Dateinamen und befinden sich im Ausgabeordner Ihres Projekts. Weitere Informationen finden Sie unter [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Hostprozessdateien (.vshost.exe) sind für die Verwendung von Visual Studio und sollten nicht direkt ausgeführt oder mit Ihrer Anwendung bereitgestellt werden.  
  
## Verbesserte Debugleistung
<a id="improved-debugging-performance" class="xliff"></a>  
 Der Hostprozess erstellt eine Anwendungsdomäne und ordnet die Anwendung dem Debugger zu. Das Ausführen dieser Aufgaben kann zu einer spürbaren Verzögerung zwischen der Zeit, wenn das Debuggen gestartet wird, und der Zeit, wenn die Anwendung beginnt, führen. Der Hostprozess hilft die Leistung durch das Erstellen der Anwendungsdomäne und das Zuordnen des Debuggers im Hintergrund zu steigern sowie durch Speichern der Anwendungsdomäne und des Debuggerzustands zwischen den Ausführungen der Anwendung. Weitere Informationen zu Anwendungsdomänen finden Sie unter [Anwendungsdomänen](/dotnet/framework/app-domains/application-domains).  
  
## Das Debuggen teilweise vertrauenswürdiger Anwendungen
<a id="partial-trust-debugging" class="xliff"></a>  
 Eine Anwendung kann auf der [Seite „Sicherheit“](../ide/reference/security-page-project-designer.md) vom **Projekt-Designer** als teilweise vertrauenswürdige Anwendung angegeben werden. Das Debuggen einer teilweise vertrauenswürdigen Anwendung erfordert spezielle Initialisierung der Anwendungsdomäne. Diese Initialisierung erfolgt über den Hostprozess.  
  
## Ausdrucksauswertung zur Entwurfszeit
<a id="design-time-expression-evaluation" class="xliff"></a>  
 Die Ausdrucksauswertung zur Entwurfszeit können Sie zum Testen von Code aus dem **direkten** Fenster verwenden, ohne die Anwendung auszuführen. Der Hostprozess führt diesen Code während der Ausdrucksauswertung zur Entwurfszeit aus. Weitere Informationen finden Sie unter [Direktfenster](../ide/reference/immediate-window.md).  
  
## Siehe auch
<a id="see-also" class="xliff"></a>  
 [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md)   
 [Vorgehensweise: Deaktivieren des Hostprozesses](../ide/how-to-disable-the-hosting-process.md)   
 [Direktfenster](../ide/reference/immediate-window.md)   
 [Anwendungsdomänen](/dotnet/framework/app-domains/application-domains)
