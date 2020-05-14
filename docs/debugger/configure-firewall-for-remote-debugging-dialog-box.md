---
title: Firewall für Remotedebuggen konfigurieren (Dialogfeld) | Microsoft-Dokumentation
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
ms.openlocfilehash: 8a2511fc2adfa63ff28f8459f48cbdf4b4623ff5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745660"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Firewall für Remotedebuggen konfigurieren (Dialogfeld)
Dieses Dialogfeld wird angezeigt, wenn von der Windows-Firewall Daten blockiert werden, die der Debugger über das Netzwerk empfangen soll. Um das Remotedebuggen fortzusetzen, müssen Sie der Firewall Ausnahmen hinzufügen und Ports öffnen, damit der Debugger Informationen empfangen kann.

> [!CAUTION]
> Wenn Sie Ports in der Firewall öffnen, ist der Computer unter Umständen Sicherheitsrisiken ausgesetzt, die sonst von der Firewall blockiert werden. Durch das Öffnen einer Lücke für das Remotedebuggen wird die Blockierung der Ports 4020 und 4021 in Visual Studio 2015 aufgehoben. In anderen Versionen von Visual Studio werden andere Portnummern verwendet. Weitere Informationen finden Sie unter [Remotedebugger – Portzuweisungen](../debugger/remote-debugger-port-assignments.md). Zusätzlich wird dem Debugger ermöglicht, weitere Ports zu öffnen. Weitere Informationen finden Sie unter [Konfigurieren der Windows-Firewall für das Remotedebuggen](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="uielement-list"></a>UIElement-Liste
 **Remotedebugging abbrechen**: Mit dieser Option wird der Remotedebugversuch abgebrochen. Die Sicherheitseinstellungen des Computers bleiben bestehen.

 **Blockierung für Remotedebugging auf Computern im lokalen Netzwerk (Subnetz) aufheben**: Aktiviert das Remotedebuggen von Computern im lokalen Subnetz. Dadurch können Sicherheitslücken in den Computern des Subnetzes entstehen, die Firewall wird jedoch weiterhin Informationen von außerhalb des Subnetzes blockieren.

 **Blockierung für Remotedebugging von beliebigem Computer aufheben**: Aktiviert das Remotedebuggen von Computern überall im Netzwerk. Diese Einstellung ist am unsichersten.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Remote Debugging](../debugger/remote-debugging.md)
- [Referenz zur Debugger-Benutzeroberfläche](../debugger/debugging-user-interface-reference.md)