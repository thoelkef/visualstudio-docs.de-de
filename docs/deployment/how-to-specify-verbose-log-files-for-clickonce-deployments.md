---
title: 'Vorgehensweise: Angeben von ausführlichen Protokolldateien für ClickOnce-Bereitstellungen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8153625ec875cb54b0fc7b626d0cef61df2e9b71
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557982"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Gewusst wie: Angeben von ausführlichen Protokolldateien für ClickOnce-Bereitstellungen
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwaltet die Aktivitätsprotokolldateien für alle Bereitstellungen an. Diese Protokolle enthalten Details zum Installieren, initialisieren, aktualisieren und Deinstallieren einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung. Um die Details zu erhöhen, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] schreibt in diese Protokolldateien verwenden den Registrierungs-Editor (**regedit.exe**) um den Ausführlichkeitsgrad anzugeben.  
  
> [!CAUTION]
>  Falsch Verwendung des Registrierungs-Editors können zu schwerwiegende Problemen führen, die möglicherweise eine Neuinstallation des Betriebssystems erforderlich sind. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.  
  
 Das folgende Verfahren beschreibt, wie die Ausführlichkeitsstufe für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Protokolldateien für den aktuellen Benutzer. Um den Ausführlichkeitsgrad zu verringern, entfernen Sie diesen Registrierungswert.  
  
### <a name="to-specify-verbose-log-files"></a>Um ausführliche Protokolldateien anzugeben.  
  
1.  Open **Regedit.exe**.  
  
2.  Navigieren Sie zum Knoten `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Erstellen Sie ggf. einen neuen Zeichenfolgenwert mit dem Namen `LogVerbosityLevel`.  
  
4.  Legen Sie die `LogVerbosityLevel` Wert `1`.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)