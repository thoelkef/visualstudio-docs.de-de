---
title: 'Fehler: Der Webserver konnte die angeforderte Ressource nicht gefunden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8769c84237d877f02b7c9d3d02c6391f9e955ff3
ms.sourcegitcommit: 40b6438b5acd7e59337a382c39ec711b9e99cc8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100977"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Fehler: Der Webserver konnte die angeforderte Ressource nicht finden
Aufgrund von Sicherheitsüberlegungen wurde von IIS ein generischer Fehler zurückgegeben.  

Eine mögliche Ursache ist die Sicherheitskonfiguration des Servers. In IIS 6.0 und früheren Versionen wurde ein Zusatzhardwareprogramm, das als URLScan bekannt ist, zum Herausfiltern verdächtiger und fehlerhafter Anforderungen verwendet. Bei IIS 7.0 ist zu diesem Zweck die Anforderungsfilterung integriert. In beiden Fällen kann übermäßig einschränkende Anforderungsfilterung Visual Studio am Debuggen des Servers hindern.  

Eine weitere mögliche Ursache dieses Fehlers ist, dass der W3SVC-Dienst für IIS nicht gestartet wurde. Überprüfen Sie, dass dieser Dienst im Fenster Dienste (abgeblendet) gestartet wurde (*"Services.msc"*).

Es gibt zahlreiche weitere mögliche Ursachen für diesen Fehler. Einige der häufigsten Ursachen schließen ein Problem mit der IIS-Installation oder der Konfigurationsroutine, der Websitekonfiguration oder den Berechtigungen im Dateisystem ein. Sie können versuchen, mit einem Browser auf die Ressource zuzugreifen. Abhängig davon, wie IIS so konfiguriert ist müssen Sie möglicherweise verwenden Sie einen lokalen Browser auf dem Server, oder überprüfen die IIS-Fehlerprotokoll, um eine detaillierte Fehlermeldung zu erhalten.  
  
 Weitere Informationen zur Problembehandlung bei IIS finden Sie unter [IIS-Verwaltung und Administration](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler: Der Webserver wurde gesperrt und blockiert das DEBUG-Verb](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)