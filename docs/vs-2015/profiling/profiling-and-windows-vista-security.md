---
title: Profilerstellung und Sicherheit in Windows Vista | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 736e7a04813a6c56d6cab6d1886171e321d583cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523346"
---
# <a name="profiling-and-windows-vista-security"></a>Profilerstellung und Sicherheit in Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Profilerstellung und Sicherheit in Windows Vista](https://docs.microsoft.com/visualstudio/profiling/profiling-and-windows-vista-security).  
  
Je nach [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)]-Einstellungen für die Benutzerzugriffsberechtigung, die ein Administrator zur Verfügung gestellt hat, kann ein einzelner Benutzer über die Sicherheitsberechtigung zur Profilerstellung eines Prozesses auf dem Computer verfügen. Die folgenden Beispiele veranschaulichen mögliche Unterschiede zwischen Benutzern:  
  
-   Einige Benutzer können auf erweiterte Profilerstellungsfeatures zugreifen, wenn der Administrator Treiber und Dienst gestartet hat.  
  
-   Domänenbenutzer können nur auf Beispiel-Profilerstellung zugreifen.  
  
-   Einige Benutzer können den Zugriff auf die Profilerstellung für alle anderen Benutzer verweigern.  
  
 Weitere Informationen finden Sie unter den ADMIN-Optionen in [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## <a name="cross-session-profiling"></a>Sitzungsübergreifende Profilerstellung  
 *Sitzungsübergreifende Profilerstellung* ist die Möglichkeit, ein Profil für einen Prozess zu erstellen, der in einer anderen Sitzung ausgeführt wird. Z.B. werden die meisten Dienste in Sitzung 0 ausgeführt, und Benutzer können nicht direkt in Sitzung 0 ausgeführt werden. Mithilfe der Schaltfläche **An den Prozess anhängen** auf der Leistungs-Explorer-Symbolleiste oder mithilfe der /Anfügen-Option vom Befehlszeilentool VSPerfCmd können Sie Profile für die meisten Prozesse in anderen Anmeldesitzungen erstellen.  
  
 Sie können eine Liste der Prozesse ansehen, die durch Festlegen der Sichtbarkeitsoptionen der prozessübergreifenden Profilerstellung verfügbar sind. Diese Optionen stehen im Fenster **An den Prozess anhängen** zur Verfügung. Dieses Fenster wird angezeigt, wenn Sie auf **An den Prozess anhängen** klicken:  
  
-   **Prozesse aller Benutzer anzeigen**  
  
     Wenn diese Option nicht ausgewählt ist, zeigt die Liste nur die Prozesse an, die dem aktuellen Benutzer gehören. Wenn **Prozesse aller Benutzer anzeigen** aktiviert ist, wird die Liste der Prozesse aller Benutzer angezeigt.  
  
-   **Prozesse in allen Sitzungen anzeigen**  
  
     Wenn diese Option nicht ausgewählt ist, zeigt die Liste Prozesse in der aktuellen Sitzung an. Wenn diese Option ausgewählt ist, zeigt die Liste Prozesse in allen Sitzungen an.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersichten](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Vorgehensweise: Anfügen an einen laufenden Prozess](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)



