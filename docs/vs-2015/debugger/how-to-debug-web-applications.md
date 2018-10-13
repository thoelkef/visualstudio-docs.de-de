---
title: 'Vorgehensweise: Debuggen von Webanwendungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e185b1b35a2462547ca8689dc1a4bfe80ff036
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260811"
---
# <a name="how-to-debug-web-applications"></a>Gewusst wie: Debuggen von Webanwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ist die haupttechnologie für die Entwicklung von Webanwendungen in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debugger bietet Ihnen leistungsfähige Tools zum Debuggen von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendungen, die lokal oder auf einem Remoteserver ausgeführt werden. Dieses Thema beschreibt das Debuggen einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Projekt während der Entwicklung. Informationen zum Debuggen einer [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Anwendung, die bereits auf einem Produktionsserver bereitgestellt wird, finden Sie unter [bereitgestellte Web-Anwendungen Debuggen](../debugger/debugging-deployed-web-applications.md).  
  
 So debuggen Sie eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Anwendung  
  
-   Sie müssen über die erforderlichen Berechtigungen verfügen. Weitere Informationen finden Sie unter [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).  
  
-   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Debuggen muss aktiviert sein, **Projekteigenschaften**.  
  
-   In der Konfigurationsdatei der Anwendung (Web.config) muss der Debugmodus festgelegt sein. Der Debugmodus veranlasst [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] zum Erstellen von Symbolen für dynamisch generierte Dateien und ermöglicht dem Debugger das Hinzufügen zur Anwendung [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] legt dies beim Starten des Debugvorgangs automatisch fest, wenn Sie das Projekt aus der Webprojekte-Vorlage erstellt haben.  
  
-   Weitere Informationen finden Sie unter [Vorgehensweise: Debuggen für ASP.NET-Anwendungen aktivieren](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>So debuggen Sie Webanwendungen während der Entwicklung  
  
1.  Auf der **Debuggen** Menü klicken Sie auf **starten** zum Debuggen der Webanwendung beginnen.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt das Webanwendungsprojekt, stellt ggf. die Anwendung bereit, startet den ASP.NET Development Server, wenn Sie lokal debuggen, und fügt sie an den [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Arbeitsprozess an.  
  
2.  Verwenden Sie den Debugger, um Haltepunkte festzulegen bzw. zu entfernen, schrittweise auszuführen und andere Debugoperationen auszuführen. Gehen Sie dabei genauso wie bei allen anderen Anwendungen vor.  
  
     Weitere Informationen finden Sie unter [Debugger – Grundlagen](../debugger/debugger-basics.md).  
  
3.  Auf der **Debuggen** Menü klicken Sie auf **Debuggen beenden** um die Debugsitzung abzuschließen, oder klicken, auf die **Datei** in Internet Explorer, klicken Sie anschließend auf **schließen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md)   
 [Debuggen von ASP.NET- und AJAX-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Gewusst wie: Debuggen für ASP.NET-Anwendungen aktivieren](../debugger/how-to-enable-debugging-for-aspnet-applications.md)



