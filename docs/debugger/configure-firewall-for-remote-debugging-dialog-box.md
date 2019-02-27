---
title: Konfigurieren der Firewall für das Remotedebuggen im Dialogfeld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75342630e347eaabe6854498c43294599afae5a5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637515"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Firewall für Remotedebuggen konfigurieren (Dialogfeld)
Dieses Dialogfeld wird angezeigt, wenn von der Windows-Firewall Daten blockiert werden, die der Debugger über das Netzwerk empfangen soll. Um das Remotedebuggen fortzusetzen, müssen Sie der Firewall Ausnahmen hinzufügen und Ports öffnen, damit der Debugger Informationen empfangen kann.

> [!CAUTION]
> Wenn Sie Ports in der Firewall öffnen, ist der Computer unter Umständen Sicherheitsrisiken ausgesetzt, die sonst von der Firewall blockiert werden. Durch das Öffnen einer Lücke für das Remotedebuggen wird die Blockierung der Ports 4020 und 4021 in Visual Studio 2015 aufgehoben. In anderen Versionen von Visual Studio werden andere Portnummern verwendet. Weitere Informationen finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md). Zusätzlich wird dem Debugger ermöglicht, weitere Ports zu öffnen. Weitere Informationen finden Sie unter [der Windows-Firewall für Remotedebuggen konfigurieren](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="uielement-list"></a>UIElement-Liste
 **Remotedebugging Abbrechen** der Remotedebugversuch abgebrochen. Die Sicherheitseinstellungen des Computers bleiben bestehen.

 **Blockierung für Remotedebugging von Computern im lokalen Netzwerk (Subnetz) aufheben** aktiviert das Remotedebugging von Computern im lokalen Subnetz. Dadurch können Sicherheitslücken in den Computern des Subnetzes entstehen, die Firewall wird jedoch weiterhin Informationen von außerhalb des Subnetzes blockieren.

 **Blockierung für Remotedebugging von einem beliebigen Computer aufheben** aktiviert das Remotedebugging von Computern im Netzwerk. Diese Einstellung ist am unsichersten.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Remote Debugging](../debugger/remote-debugging.md)
- [Referenz zur Debugger-Benutzeroberfläche](../debugger/debugging-user-interface-reference.md)