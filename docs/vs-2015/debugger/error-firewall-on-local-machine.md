---
title: 'Fehler: Firewall auf dem lokalen Computer | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cbca2e944e7313e54fd469dd41774f40931ee3d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245348"
---
# <a name="error-firewall-on-local-machine"></a>Fehler: Firewall auf lokalem Computer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Internetverbindungsfirewall auf dem lokalen Computer, auf dem Sie Visual Studio ausführen, ist nicht für Remotedebuggen eingerichtet. Für das Remotedebuggen von verwaltetem oder systemeigenem Code mit dem Standardtransport muss der TCP-Anschluss 135 für den DCOM-Datentransfer geöffnet werden. Datei- und Druckerfreigabe müssen geöffnet werden, und devenv.exe muss der Ausnahmenliste hinzugefügt werden. Es ist möglicherweise auch erforderlich, einige IPSEC-Anschlüsse zu öffnen.  
  
 Weitere Informationen finden Sie unter [festgelegt Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).



