---
title: 'Fehler: Firewall auf lokalem Computer | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a1813410a092ced335f37b9df4cf6547ca1cc3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851048"
---
# <a name="error-firewall-on-local-machine"></a>Fehler: Firewall auf lokalem Computer
Die Internetverbindungsfirewall auf dem lokalen Computer, auf dem Sie Visual Studio ausführen, ist nicht für Remotedebuggen eingerichtet. Für das Remotedebuggen von verwaltetem oder systemeigenem Code mit dem Standardtransport muss der TCP-Anschluss 135 für den DCOM-Datentransfer geöffnet werden. Datei- und Druckerfreigabe müssen geöffnet werden, und devenv.exe muss der Ausnahmenliste hinzugefügt werden. Es ist möglicherweise auch erforderlich, einige IPSEC-Anschlüsse zu öffnen.

 Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).