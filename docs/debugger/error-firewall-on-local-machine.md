---
title: 'Fehler: Firewall auf dem lokalen Computer | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0eb7158fe2274fbe8707a147fe63a0937689d23
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="error-firewall-on-local-machine"></a>Fehler: Firewall auf lokalem Computer
Die Internetverbindungsfirewall auf dem lokalen Computer, auf dem Sie Visual Studio ausführen, ist nicht für Remotedebuggen eingerichtet. Für das Remotedebuggen von verwaltetem oder systemeigenem Code mit dem Standardtransport muss der TCP-Anschluss 135 für den DCOM-Datentransfer geöffnet werden. Datei- und Druckerfreigabe müssen geöffnet werden, und devenv.exe muss der Ausnahmenliste hinzugefügt werden. Es ist möglicherweise auch erforderlich, einige IPSEC-Anschlüsse zu öffnen.  
  
 Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).