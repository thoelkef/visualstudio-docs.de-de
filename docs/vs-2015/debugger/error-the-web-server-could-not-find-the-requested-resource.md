---
title: 'Fehler: der Webserver konnte die angeforderte Ressource nicht finden. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 555bb56ee84b7bc48f6b6453c11daef366f97e49
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845120"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Fehler: Der Webserver konnte die angeforderte Ressource nicht finden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aufgrund von Sicherheitsüberlegungen wurde von IIS ein generischer Fehler zurückgegeben.  
  
 Eine mögliche Ursache ist die Sicherheitskonfiguration des Servers. In IIS 6.0 und früheren Versionen wurde ein Zusatzhardwareprogramm, das als URLScan bekannt ist, zum Herausfiltern verdächtiger und fehlerhafter Anforderungen verwendet. Bei IIS 7.0 ist zu diesem Zweck die Anforderungsfilterung integriert. In beiden Fällen kann übermäßig einschränkende Anforderungsfilterung Visual Studio am Debuggen des Servers hindern.  
  
 Für diesen Fehler sind viele Ursachen möglich. Einige der häufigsten Ursachen schließen ein Problem mit der IIS-Installation oder der Konfigurationsroutine, der Websitekonfiguration oder den Berechtigungen im Dateisystem ein. Sie können versuchen, mit einem Browser auf die Ressource zuzugreifen. Abhängig von der IIS-Konfiguration müssen Sie möglicherweise einen lokalen Browser auf dem Server verwenden oder das IIS-Fehlerprotokoll überprüfen, um eine ausführliche Fehlermeldung zu erhalten.  
  
 Weitere Informationen über die Problembehandlung bei IIS finden Sie unter [IIS-Verwaltung](https://www.iis.net/learn/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Siehe auch  
 [URLScan-Sicherheits Tool](/iis/extensions/working-with-urlscan/urlscan-3-reference)   
 [Fehler: Der Webserver wurde gesperrt und blockiert das DEBUG-Verb](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
