---
title: Übersicht über die ClickOnce-Cache | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ff72cd106f39b4573a0e1d61715dad4f8c65140
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-cache-overview"></a>Übersicht über den ClickOnce-Cache
Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen an, ob sie lokal installiert oder online gehostet werden auf dem Clientcomputer gespeichert eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Anwendung *Cache*. Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Cache ist eine Familie von ausgeblendeten Verzeichnisse unter dem Verzeichnis "Local Settings" des Ordners für den aktuellen Benutzer Dokumente und Einstellungen. Dieser Cache enthält Dateien für alle der Anwendung, einschließlich der Assemblys, die Konfigurationsdateien, die Anwendung und die benutzereinstellungen und die Datenverzeichnis. Der Cache ist auch für die Migration von Daten im Verzeichnis der Anwendung auf die neueste Version verantwortlich. Weitere Informationen zur Datenmigration finden Sie unter [zugreifen auf lokale und Remotedaten in ClickOnce-Anwendungen](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Durch die Bereitstellung von eines zentralen Ort für Anwendungsspeicher, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] übernimmt die Aufgabe des Verwaltens von der physischen Installations einer Anwendung des Benutzers. Der Cache hilft außerdem beim Isolieren von Anwendungen, bleiben die Assemblys und die Datendateien für alle Anwendungen und ihre Versionen auszuweiten, distinct voneinander zu trennen. Beispielsweise, wenn Sie ein upgrade einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, auf die Version und die zugehörigen Datenressourcen mit ihren eigenen Verzeichnissen im Cache bereitgestellt werden.  
  
## <a name="cache-storage-quota"></a>Cache-Speicherkontingent  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, die online gehostet werden, sind eingeschränkte hinsichtlich der Menge an Speicherplatz, die sie belegen können ein Kontingent, die die Größe des einschränkt der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Cache. Die Cachegröße gilt für alle Benutzer onlineanwendungen; eine einzelne, online, teilweise vertrauenswürdigen Anwendung ist auf die Hälfte des Speicherplatzes Kontingent einnimmt beschränkt. Installierte Anwendungen werden nicht durch die Cachegröße eingeschränkt und zählen nicht bei der cachegrenzwert. Für alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, den Cache behält nur die aktuelle Version und die zuvor installierte Version.  
  
 Standardmäßig Clientcomputer verfügen, auf 250 MB Speicher für online [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen. Datendateien zählen nicht auf diesem Grenzwert angerechnet. Ein Systemadministrator kann vergrößern oder verkleinern dieses Kontingent auf einem bestimmten Client-Computer durch Ändern des Registrierungsschlüssels einen DWORD-Wert ist HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB die drückt der Cachegröße in KB. Beispielsweise wird die Cachegröße auf 50 MB zu reduzieren, dieser Wert in 51200 geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)