---
title: Übersicht über die ClickOnce-Cache | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58ea758ea10e2c58ff123a2bc991f14191db0aa1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961229"
---
# <a name="clickonce-cache-overview"></a>Übersicht über den ClickOnce-Cache
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alle [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen an, ob sie lokal installiert oder online gehostete befinden sich auf dem Clientcomputer in einem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Anwendung *Cache*. Ein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Cache ist eine verborgene Verzeichnisse im Verzeichnis lokalen Einstellungen des aktuellen Benutzers Ordner "Dokumente und Einstellungen". Dieser Cache enthält alle die Dateien der Anwendung, einschließlich Assemblys, Konfigurationsdateien, Anwendung und der benutzereinstellungen und Verzeichnis "Data". Der Cache ist auch zuständig für die Migration von Daten im Verzeichnis der Anwendung auf die neueste Version. Weitere Informationen zur Datenmigration finden Sie unter [zugreifen auf lokale und Remotedaten in ClickOnce-Anwendungen](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Durch die Bereitstellung von eines zentralen Ort für Anwendungsspeicher [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] übernimmt die Aufgabe der Verwaltung der physischen Installations einer Anwendung des Benutzers. Der Cache kann auch die Anwendungen zu isolieren, indem die Assemblys und die Datendateien für alle Anwendungen und die unterschiedlichen Versionen voneinander zu trennen. Z. B. Wenn Sie ein upgrade einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung, dass die Version und die Datenressourcen eigene Verzeichnisse im Cache angegeben werden.  
  
## <a name="cache-storage-quota"></a>Cache des Speicherkontingents  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen, die online gehostet werden, sind hinsichtlich der Menge des Speicherplatzes, die sie belegen können durch ein Kontingent, die die Größe des einschränkt beschränkt die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Cache. Die Cachegröße gilt für onlineanwendungen des Benutzers. eine einzelne, online, teilweise vertrauenswürdigen Anwendung ist, belegt die Hälfte des Speicherplatzes Kontingent beschränkt. Installierte Anwendungen werden nicht durch die Cachegröße eingeschränkt und zählen nicht bei Cache-Beschränkung. Für alle [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen, die den Cache behält nur die aktuelle Version und die zuvor installierte Version.  
  
 In der Standardeinstellung Clientcomputer verfügen, auf 250 MB Speicher online [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen. Datendateien werden für diesen Grenzwert nicht berücksichtigt. Ein Systemadministrator kann vergrößern oder verkleinern dieses Kontingent für einen bestimmten Clientcomputer, ändern Sie den Registrierungsschlüssel einen DWORD-Wert ist HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB drückt aus, die die Cachegröße in KB. Um die Cachegröße auf 50 MB zu reduzieren, würden Sie beispielsweise diesen Wert in 51200 ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
