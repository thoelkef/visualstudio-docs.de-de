---
title: 'Fehler: Der Webserver konnte die angeforderte Ressource nicht gefunden | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cba31527af469b897ae178b6b0f810840b7d9cd2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035483"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Fehler: Der Webserver konnte die angeforderte Ressource nicht finden
Aufgrund von Sicherheitsüberlegungen wurde von IIS ein generischer Fehler zurückgegeben.  

Eine mögliche Ursache ist die Sicherheitskonfiguration des Servers. In IIS 6.0 und früheren Versionen wurde ein Zusatzhardwareprogramm, das als URLScan bekannt ist, zum Herausfiltern verdächtiger und fehlerhafter Anforderungen verwendet. Bei IIS 7.0 ist zu diesem Zweck die Anforderungsfilterung integriert. In beiden Fällen kann übermäßig einschränkende Anforderungsfilterung Visual Studio am Debuggen des Servers hindern.  

Eine weitere mögliche Ursache dieses Fehlers ist, dass der W3SVC-Dienst für IIS nicht gestartet wurde. Überprüfen Sie, dass dieser Dienst im Fenster Dienste (abgeblendet) gestartet wurde (*"Services.msc"*).

Es gibt zahlreiche weitere mögliche Ursachen für diesen Fehler. Einige der häufigsten Ursachen schließen ein Problem mit der IIS-Installation oder der Konfigurationsroutine, der Websitekonfiguration oder den Berechtigungen im Dateisystem ein. Sie können versuchen, mit einem Browser auf die Ressource zuzugreifen. Abhängig von der IIS-Konfiguration müssen Sie möglicherweise einen lokalen Browser auf dem Server verwenden oder das IIS-Fehlerprotokoll überprüfen, um eine ausführliche Fehlermeldung zu erhalten.  
  
 Weitere Informationen über die Problembehandlung bei IIS finden Sie unter [IIS-Verwaltung](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler: Der Webserver wurde gesperrt und blockiert das DEBUG-Verb](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)