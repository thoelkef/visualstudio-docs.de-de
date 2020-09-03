---
title: 'Gewusst wie: Debuggen von Webanwendungen | Microsoft-Dokumentation'
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
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205400"
---
# <a name="how-to-debug-web-applications"></a>Gewusst wie: Debuggen von Webanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ist die primäre Technologie zum Entwickeln von Webanwendungen in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debugger bietet Ihnen leistungsfähige Tools zum Debuggen von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen, die lokal oder auf einem Remoteserver ausgeführt werden. In diesem Thema wird das Debuggen eines [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Projekts während der Entwicklung beschrieben. Informationen zum [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Debuggen einer Webanwendung, die bereits auf einem Produktionsserver bereitgestellt wurde, finden Sie unter Debugging bereitgestellter [Webanwendungen](../debugger/debugging-deployed-web-applications.md)  
  
 So debuggen Sie eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendung  
  
- Sie müssen über die erforderlichen Berechtigungen verfügen. Weitere Informationen finden Sie unter [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] das Debuggen muss in den **Projekteigenschaften**aktiviert werden.  
  
- In der Konfigurationsdatei der Anwendung (Web.config) muss der Debugmodus festgelegt sein. Der Debugmodus veranlasst [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] zum Erstellen von Symbolen für dynamisch generierte Dateien und ermöglicht dem Debugger das Hinzufügen zur Anwendung [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] legt dies beim Starten des Debugvorgangs automatisch fest, wenn Sie das Projekt aus der Webprojekte-Vorlage erstellt haben.  
  
- Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren des Debuggens für ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>So debuggen Sie Webanwendungen während der Entwicklung  
  
1. Klicken Sie im Menü **Debuggen** auf starten, um das Debugging der Webanwendung zu **starten** .  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt das Webanwendungs Projekt, stellt die Anwendung bei Bedarf bereit, startet die ASP.NET Development Server, wenn Sie lokal debuggen, und fügt Sie an den Arbeits [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Prozess an.  
  
2. Verwenden Sie den Debugger, um Haltepunkte festzulegen bzw. zu entfernen, schrittweise auszuführen und andere Debugoperationen auszuführen. Gehen Sie dabei genauso wie bei allen anderen Anwendungen vor.  
  
     Weitere Informationen finden Sie unter [Grundlagen des Debuggers](../debugger/debugger-basics.md).  
  
3. Klicken Sie im Menü **Debuggen** auf **Debuggen** beenden, um die Debugsitzung zu beenden, oder klicken Sie im Menü **Datei** von Internet Explorer auf **Schließen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Webanwendungen und Skript Debuggen](../debugger/debugging-web-applications-and-script.md)   
 [Debugging von ASP.net-und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [How to: Debuggen für ASP.NET-Anwendungen aktivieren](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
