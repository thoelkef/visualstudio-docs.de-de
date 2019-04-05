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
ms.openlocfilehash: 0efd71b38d3fcd8ae8241e31e721bd48e857d3bd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946514"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Vorgehensweise: Angeben von ausführlichen Protokolldateien für ClickOnce-Bereitstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] verwaltet die Aktivitätsprotokolldateien für alle Bereitstellungen an. Diese Protokolle enthalten Details zu installieren, initialisiert werden, aktualisieren und Deinstallieren einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung. Um die Details zu erhöhen, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Schreibvorgänge für diese Protokolldateien verwenden die Registrierungs-Editor (**regedit.exe**) an den Ausführlichkeitsgrad.  
  
> [!CAUTION]
>  Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, können Sie schwerwiegenden Problemen führen, die Neuinstallation des Betriebssystems erforderlich machen können. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.  
  
 Das folgende Verfahren beschreibt, wie Sie an die Ausführlichkeitsstufe für [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Protokolldateien für den aktuellen Benutzer. Um der Ausführlichkeitsgrad zu reduzieren, entfernen Sie diesen Registrierungswert.  
  
### <a name="to-specify-verbose-log-files"></a>Angeben von ausführlichen Protokolldateien  
  
1.  Open **Regedit.exe**.  
  
2.  Navigieren Sie zum Knoten `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Erstellen Sie einen neuen Zeichenfolgenwert mit dem Namen, ggf. `LogVerbosityLevel`.  
  
4.  Legen Sie den Wert `LogVerbosityLevel` auf `1` fest.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)
