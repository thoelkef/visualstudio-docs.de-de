---
title: Debuggen bereitgestellter Webanwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9608643801255d6c2cbf278cbfd96908f1f3911d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444074"
---
# <a name="debugging-deployed-web-applications"></a>Debuggen bereitgestellter Webanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine Webanwendung debuggen müssen, die auf einem Produktionsserver ausgeführt wird, sollten Sie besondere Vorsicht walten lassen. Wenn der Debugger an den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess angehängt wird, wird z. B. beim Erreichen eines Haltepunkts der gesamte verwaltete Code im Arbeitsprozess angehalten. Das Anhalten des gesamten verwalteten Codes im Arbeitsprozess kann zu einem Arbeitsstopp für alle Benutzer des Servers führen. Wenn Sie auf einem Produktionsserver debuggen, müssen Sie unter allen Umständen die möglichen Auswirkungen auf die Produktion beachten.  
  
 Um eine bereitgestellte und ausgeführte Anwendung über [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zu debuggen, müssen Sie den Debugger an den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess anhängen und sicherstellen, dass der Debugger auf Symbole für die Anwendung zugreifen kann. Außerdem müssen Sie die Quelldateien für die Anwendung lokalisieren und öffnen. Weitere Informationen finden Sie unter [angeben von Symbol (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Vorgehensweise: Herausfinden des ASP.NET-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md), und [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
> Viele [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen verweisen auf DLLs, die Geschäftslogik oder sonstigen nützlichen Code enthalten. Durch einen solchen Verweis wird die DLL automatisch vom lokalen Computer in den Ordner \bin des virtuellen Verzeichnisses der Webanwendung kopiert. Beim Debuggen sollten Sie beachten, dass die Webanwendung nicht auf die Kopie der DLL auf dem lokalen Computer, sondern auf diese Kopie der DLL verweist.  
  
 Das Anhängen an den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess unterscheidet sich nicht vom Anhängen an einen beliebigen anderen Remoteprozess. Wenn das passende Projekt nicht geöffnet ist, wird nach dem Anhängen ein Dialogfeld angezeigt, sobald die Anwendung unterbrochen wird. Dieses Dialogfeld fordert Sie auf, den Speicherort der Quelldateien der Anwendung anzugeben. Der im Dialogfeld eingegebene Dateiname muss mit dem Dateinamen übereinstimmen, der in den Debugsymbolen (auf dem Webserver) angegeben ist. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md)   
 [Vorgehensweise: Debuggen für ASP.NET-Anwendungen aktivieren](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Vorgehensweise: Herausfinden des ASP.NET-Prozessnamens](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
