---
title: 'Vorgehensweise: Angeben von ausführlichen Protokolldateien für ClickOnce-Bereitstellungen | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc7fbdace660a894352623a3ff8765a165b5556
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619497"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Vorgehensweise: Angeben von ausführlichen Protokolldateien für ClickOnce-Bereitstellungen
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwaltet die Aktivitätsprotokolldateien für alle Bereitstellungen an. Diese Protokolle enthalten Details zu installieren, initialisiert werden, aktualisieren und Deinstallieren einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung. Um die Details zu erhöhen, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Schreibvorgänge für diese Protokolldateien verwenden die Registrierungs-Editor (*regedit.exe*) an den Ausführlichkeitsgrad.

> [!CAUTION]
>  Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, können Sie schwerwiegenden Problemen führen, die Neuinstallation des Betriebssystems erforderlich machen können. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.

 Das folgende Verfahren beschreibt, wie Sie an die Ausführlichkeitsstufe für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Protokolldateien für den aktuellen Benutzer. Um der Ausführlichkeitsgrad zu reduzieren, entfernen Sie diesen Registrierungswert.

### <a name="to-specify-verbose-log-files"></a>Angeben von ausführlichen Protokolldateien

1.  Open *Regedit.exe*.

2.  Navigieren Sie zum Knoten **HKEY_CURRENT_USERSoftware\Microsoft\Windows\CurrentVersion\Deployment**.

3.  Erstellen Sie einen neuen Zeichenfolgenwert mit dem Namen, ggf. `LogVerbosityLevel`.

4.  Legen Sie den Wert `LogVerbosityLevel` auf `1` fest.

## <a name="see-also"></a>Siehe auch
- [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)