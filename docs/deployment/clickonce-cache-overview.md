---
title: Übersicht über die ClickOnce-Cache | Microsoft-Dokumentation
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85dbe4917d37c8d39dd8348c32d88933032ede1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900534"
---
# <a name="clickonce-cache-overview"></a>Übersicht über den ClickOnce-Cache
Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen an, ob sie lokal installiert oder online gehostete befinden sich auf dem Clientcomputer in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Anwendung *Cache*. Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Cache ist eine verborgene Verzeichnisse im Verzeichnis lokalen Einstellungen des aktuellen Benutzers Ordner "Dokumente und Einstellungen". Dieser Cache enthält alle die Dateien der Anwendung, einschließlich Assemblys, Konfigurationsdateien, Anwendung und der benutzereinstellungen und Verzeichnis "Data". Der Cache ist auch zuständig für die Migration von Daten im Verzeichnis der Anwendung auf die neueste Version. Weitere Informationen zur Datenmigration finden Sie unter [zugreifen auf lokale und Remotedaten in ClickOnce-Anwendungen](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

 Durch die Bereitstellung von eines zentralen Ort für Anwendungsspeicher [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] übernimmt die Aufgabe der Verwaltung der physischen Installations einer Anwendung des Benutzers. Der Cache kann auch die Anwendungen zu isolieren, indem die Assemblys und die Datendateien für alle Anwendungen und die unterschiedlichen Versionen voneinander zu trennen. Z. B. Wenn Sie ein upgrade einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, dass die Version und die Datenressourcen eigene Verzeichnisse im Cache angegeben werden.

## <a name="cache-storage-quota"></a>Cache des Speicherkontingents
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, die online gehostet werden, sind hinsichtlich der Menge des Speicherplatzes, die sie belegen können durch ein Kontingent, die die Größe des einschränkt beschränkt die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Cache. Die Cachegröße gilt für onlineanwendungen des Benutzers. eine einzelne, online, teilweise vertrauenswürdigen Anwendung ist, belegt die Hälfte des Speicherplatzes Kontingent beschränkt. Installierte Anwendungen werden nicht durch die Cachegröße eingeschränkt und zählen nicht bei Cache-Beschränkung. Für alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen, die den Cache behält nur die aktuelle Version und die zuvor installierte Version.

 In der Standardeinstellung Clientcomputer verfügen, auf 250 MB Speicher online [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen. Datendateien werden für diesen Grenzwert nicht berücksichtigt. Ein Systemadministrator kann vergrößern oder verkleinern Sie dieses Kontingent für einen bestimmten Clientcomputer, ändern Sie den Registrierungsschlüssel **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB**, d.h. einen DWORD-Wert, der die Cachegröße in KB ausdrückt. Um die Cachegröße auf 50 MB zu reduzieren, würden Sie beispielsweise diesen Wert in 51200 ändern.

## <a name="see-also"></a>Siehe auch
- [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)