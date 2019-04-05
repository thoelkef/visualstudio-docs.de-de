---
title: 'Fehler: Firewall auf lokalem Computer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 23290ebb12c2cb3e6bb12554aa9fbb89c4fb82fa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958298"
---
# <a name="error-firewall-on-local-machine"></a>Fehler: Firewall auf lokalem Computer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Internetverbindungsfirewall auf dem lokalen Computer, auf dem Sie Visual Studio ausführen, ist nicht für Remotedebuggen eingerichtet. Für das Remotedebuggen von verwaltetem oder systemeigenem Code mit dem Standardtransport muss der TCP-Anschluss 135 für den DCOM-Datentransfer geöffnet werden. Datei- und Druckerfreigabe müssen geöffnet werden, und devenv.exe muss der Ausnahmenliste hinzugefügt werden. Es ist möglicherweise auch erforderlich, einige IPSEC-Anschlüsse zu öffnen.  
  
 Weitere Informationen finden Sie unter [festgelegt Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).
