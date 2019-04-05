---
title: 'Fehler: Keine Authentifizierung Firewall | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ad413f3e958fa6dc8edd22ef4be1428b6941bd6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961363"
---
# <a name="error-firewall-no-authentication"></a>Fehler: Firewall und „Keine Authentifizierung“
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Internetverbindungsfirewall auf dem Remotecomputer wurde nicht für das Remotedebuggen eingerichtet. Für das Remotedebuggen mit `No Authentication` muss der Ausnahmenliste die Datei msvsmon.exe hinzugefügt werden. Es ist möglicherweise auch erforderlich, einige IPSEC-Anschlüsse zu öffnen.  
  
> [!NOTE]
>  Der Remotedebugger kann die Windows Firewall automatisch konfigurieren. Wenn eine andere Firewall als die Windows Firewall verwendet wird, wie z. B. eine Software- oder Hardwarefirewall eines Drittanbieters, muss die Firewall manuell konfiguriert werden, um das Remotedebugging zu ermöglichen. Lassen Sie hierzu Verkehr für die TCP/IP-Ports zu, die von msvsmon.exe abgehört werden. Standardmäßig handelt es sich hierbei um Ports 4018 und 4019, wobei 4018 auf allen Betriebssystemen und 4019 wird nur unter Windows x64 verwendet wird, um Debugging von x86-Prozessen zu ermöglichen.  
  
 Weitere Informationen finden Sie unter [festgelegt Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).
