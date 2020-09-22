---
title: 'Gewusst wie: Angeben von ausführlichen Protokolldateien für ClickOnce-bereit Stellungen | Microsoft-Dokumentation'
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
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841282"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Gewusst wie: Angeben von ausführlichen Protokolldateien für ClickOnce-Bereitstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] verwaltet Aktivitätsprotokoll Dateien für alle bereit Stellungen. Diese Protokolle enthalten Dokument Details zum Installieren, initialisieren, aktualisieren und Deinstallieren einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung. Um die Details zu erhöhen, die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] in diese Protokolldateien geschrieben werden, verwenden Sie den Registrierungs-Editor (**regedit.exe**), um den ausführlichkeits Grad anzugeben.  
  
> [!CAUTION]
> Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, kann dies zu schwerwiegenden Problemen führen, die möglicherweise eine Neuinstallation des Betriebssystems erforderlich machen. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.  
  
 Im folgenden Verfahren wird beschrieben, wie Sie den ausführlichkeits Grad für [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Protokolldateien für den aktuellen Benutzer angeben. Entfernen Sie diesen Registrierungs Wert, um den ausführlichkeits Grad zu verringern.  
  
### <a name="to-specify-verbose-log-files"></a>So geben Sie ausführliche Protokolldateien an  
  
1. Öffnen Sie **Regedit.exe**.  
  
2. Navigieren Sie zum Knoten `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Erstellen Sie ggf. einen neuen Zeichen folgen Wert mit dem Namen `LogVerbosityLevel` .  
  
4. Legen Sie den Wert `LogVerbosityLevel` auf `1` fest.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)
