---
title: "Fehler: Eine Sicherheitsprüfung ist fehlgeschlagen, da der IIS-Admin-Dienst nicht antwortete | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bc147c979357934d68692ea863c665422c84b34
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Fehler: Fehler bei einer Sicherheitsüberprüfung, weil der IIS-Verwaltungsdienst nicht reagiert hat
Dieser Fehler tritt auf, wenn der IIS-Verwaltungsdienst nicht reagiert. Normalerweise weist dies auf ein Problem mit der IIS-Installation hin. Überprüfen Sie, dass der Dienst ausgeführt wird, mithilfe der **Services** -tool vom **Verwaltung**.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Installieren Sie IIS mithilfe der **Software** Systemsteuerung.  
  
-   - oder -   
  
-   IIS in der Systemsteuerung über die Option Software vom Computer entfernen. Wenn Sie IIS entfernt haben und die Probleme weiterhin auftreten, vergewissern Sie sich in der Registrierung, dass der folgende Schlüssel nicht mehr existiert:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     - oder -   
  
-   Deaktivieren Sie den IIS-Verwaltungsdienst in der Systemsteuerung über die Option Verwaltung. Dadurch wird IIS auf dem Computer deaktiviert.  
  
     Sie müssen den Computer nach jedem dieser drei Schritte neu starten.  
  
     Weitere Informationen finden Sie in der IIS-Dokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)