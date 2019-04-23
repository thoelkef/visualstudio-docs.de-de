---
title: 'Vorgehensweise: Angeben von ausführlichen Protokolldateien für ClickOnce-Bereitstellungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e200d0918e3d346f71da6ec2184e07e7d8433174
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069769"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Vorgehensweise: Angeben von ausführlichen Protokolldateien für ClickOnce-Bereitstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] verwaltet die Aktivitätsprotokolldateien für alle Bereitstellungen an. Diese Protokolle enthalten Details zu installieren, initialisiert werden, aktualisieren und Deinstallieren einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung. Um die Details zu erhöhen, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Schreibvorgänge für diese Protokolldateien verwenden die Registrierungs-Editor (**regedit.exe**) an den Ausführlichkeitsgrad.  
  
> [!CAUTION]
>  Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, können Sie schwerwiegenden Problemen führen, die Neuinstallation des Betriebssystems erforderlich machen können. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.  
  
 Das folgende Verfahren beschreibt, wie Sie an die Ausführlichkeitsstufe für [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Protokolldateien für den aktuellen Benutzer. Um der Ausführlichkeitsgrad zu reduzieren, entfernen Sie diesen Registrierungswert.  
  
### <a name="to-specify-verbose-log-files"></a>Angeben von ausführlichen Protokolldateien  
  
1. Open **Regedit.exe**.  
  
2. Navigieren Sie zum Knoten `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3. Erstellen Sie einen neuen Zeichenfolgenwert mit dem Namen, ggf. `LogVerbosityLevel`.  
  
4. Legen Sie den Wert `LogVerbosityLevel` auf `1` fest.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)
