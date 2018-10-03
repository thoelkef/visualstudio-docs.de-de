---
title: Konfigurieren der Firewall für das Remotedebuggen im Dialogfeld | Microsoft-Dokumentation
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
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e53e4573de1fb80d33b387e97b6ddd23b54bbb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524664"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Firewall für Remotedebuggen konfigurieren (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Konfigurieren der Firewall für Remote Debugging (Dialogfeld)](https://docs.microsoft.com/visualstudio/debugger/configure-firewall-for-remote-debugging-dialog-box).  
  
Dieses Dialogfeld wird angezeigt, wenn von der Windows-Firewall Daten blockiert werden, die der Debugger über das Netzwerk empfangen soll. Um das Remotedebuggen fortzusetzen, müssen Sie der Firewall Ausnahmen hinzufügen und Ports öffnen, damit der Debugger Informationen empfangen kann.  
  
> [!CAUTION]
>  Wenn Sie Ports in der Firewall öffnen, ist der Computer unter Umständen Sicherheitsrisiken ausgesetzt, die sonst von der Firewall blockiert werden. Durch das Öffnen einer Lücke für das Remotedebuggen wird die Blockierung der Ports 4020 und 4021 in Visual Studio 2015 aufgehoben. In anderen Versionen von Visual Studio werden andere Portnummern verwendet. Weitere Informationen finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md). Zusätzlich wird dem Debugger ermöglicht, weitere Ports zu öffnen. Weitere Informationen finden Sie unter [der Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Remotedebugging Abbrechen**  
 Mit dieser Option wird der Remotedebugversuch abgebrochen. Die Sicherheitseinstellungen des Computers bleiben bestehen.  
  
 **Blockierung für aufheben Sie Remotedebugging von Computern im lokalen Netzwerk (Subnetz)**  
 Mit dieser Option wird das Remotedebuggen der Computer im lokalen Subnetz aktiviert. Dadurch können Sicherheitslücken in den Computern des Subnetzes entstehen, die Firewall wird jedoch weiterhin Informationen von außerhalb des Subnetzes blockieren.  
  
 **Blockierung für aufheben Sie Remotedebugging von einem beliebigen computer**  
 Mit dieser Option wird das Remotedebuggen von jedem möglichen Computer aus dem Netzwerk aktiviert. Diese Einstellung ist am unsichersten.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Referenz zur Debugger-Benutzeroberfläche](../debugger/debugging-user-interface-reference.md)



