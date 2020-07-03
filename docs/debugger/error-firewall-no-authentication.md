---
title: 'Fehler: Firewall und „Keine Authentifizierung“ | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.noauth
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
ms.openlocfilehash: 199e3b203ff73397a49c19a736a447f5823e5422
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460764"
---
# <a name="error-firewall-no-authentication"></a>Fehler: Firewall und „Keine Authentifizierung“
Die Internetverbindungsfirewall auf dem Remotecomputer wurde nicht für das Remotedebuggen eingerichtet. Für das Remotedebuggen mit `No Authentication` muss der Ausnahmenliste die Datei msvsmon.exe hinzugefügt werden. Es ist möglicherweise auch erforderlich, einige IPSEC-Anschlüsse zu öffnen.

> [!NOTE]
> Der Remotedebugger kann die Windows Firewall automatisch konfigurieren. Wenn eine andere Firewall als die Windows Firewall verwendet wird, wie z. B. eine Software- oder Hardwarefirewall eines Drittanbieters, muss die Firewall manuell konfiguriert werden, um das Remotedebugging zu ermöglichen. Lassen Sie hierzu Verkehr für die TCP/IP-Ports zu, die von msvsmon.exe abgehört werden. Standardmäßig handelt es sich hierbei um Ports 4018 und 4019, wobei 4018 auf allen Betriebssystemen und 4019 wird nur unter Windows x64 verwendet wird, um Debugging von x86-Prozessen zu ermöglichen.

 Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).