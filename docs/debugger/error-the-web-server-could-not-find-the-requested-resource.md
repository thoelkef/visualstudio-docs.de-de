---
title: Der Webserver konnte die angeforderte Ressource nicht finden | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 3eaa6b3e0cc609c382e8f94383a6bdb6041a2288
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90850955"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Fehler: Der Webserver konnte die angeforderte Ressource nicht finden
Aufgrund von Sicherheitsüberlegungen wurde von IIS ein generischer Fehler zurückgegeben.

Eine mögliche Ursache ist die Sicherheitskonfiguration des Servers. In IIS 6.0 und früheren Versionen wurde ein Zusatzhardwareprogramm, das als URLScan bekannt ist, zum Herausfiltern verdächtiger und fehlerhafter Anforderungen verwendet. Bei IIS 7.0 ist zu diesem Zweck die Anforderungsfilterung integriert. In beiden Fällen kann übermäßig einschränkende Anforderungsfilterung Visual Studio am Debuggen des Servers hindern.

Eine weitere mögliche Ursache für diesen Fehler besteht darin, dass der W3SVC-Dienst für IIS nicht gestartet wurde. Überprüfen Sie im Fenster „Dienste“, ob dieser Dienst (*services.msc*) gestartet wurde (ausgegraut ist).

Für diesen Fehler sind viele weitere Ursachen möglich. Einige der häufigsten Ursachen schließen ein Problem mit der IIS-Installation oder der Konfigurationsroutine, der Websitekonfiguration oder den Berechtigungen im Dateisystem ein. Sie können versuchen, mit einem Browser auf die Ressource zuzugreifen. Abhängig von der IIS-Konfiguration müssen Sie möglicherweise einen lokalen Browser auf dem Server verwenden oder das IIS-Fehlerprotokoll überprüfen, um eine ausführliche Fehlermeldung zu erhalten.

 Weitere Informationen über die Problembehandlung bei IIS finden Sie unter [IIS-Verwaltung](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).

## <a name="see-also"></a>Siehe auch
- [Fehler: Der Webserver wurde gesperrt und blockiert das DEBUG-Verb](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)