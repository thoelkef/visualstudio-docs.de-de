---
title: "ClickOnce Cache Overview | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Windows applications, ClickOnce deployemtn"
  - "ClickOnce applications, cache"
  - "ClickOnce deployment, cache"
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce Cache Overview
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen, ob lokal installiert oder online gehostet, werden auf dem Clientcomputer in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungs*cache* gespeichert.  Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Cache stellt im Ordner Dokumente und Einstellungen des aktuellen Benutzers unter dem Verzeichnis Lokale Einstellungen eine Gruppe ausgeblendeter Verzeichnisse dar.  Dieser Cache enthält alle Anwendungsdateien, d. h. Assemblys, Konfigurationsdateien, Anwendungs\- und Benutzereinstellungen sowie das Datenverzeichnis.  Der Cache wird auch verwendet, um das Datenverzeichnis der Anwendung zur neuesten Version zu migrieren.  Weitere Informationen zur Datenmigration finden Sie unter [Zugreifen auf lokale und Remotedaten in einer ClickOnce\-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Durch die Bereitstellung eines zentralen Speicherorts für Anwendungen übernimmt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Verwaltung der physikalischen Installation einer Anwendung, sodass der Benutzer sich nicht mehr darum kümmern muss.  Zudem trägt der Cache zur Sicherstellung der Anwendungsisolation bei, da Assemblys und Datendateien aller Anwendungen sowie die verschiedenen Versionen jeweils separat gespeichert werden.  Wenn Sie bei einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung ein Upgrade durchführen, werden für die jeweilige Version und die zugehörigen Datenressourcen beispielsweise eigene Verzeichnisse im Cache bereitgestellt.  
  
## Cachespeicherkontingent  
 Der Speicherplatz, den online gehostete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen einnehmen können, ist durch ein Kontingent geregelt, durch das die Größe des [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Caches beschränkt wird.  Die Cachegröße gilt für alle Onlineanwendungen des Benutzers. Eine einzelne, teilweise vertrauenswürdige Onlineanwendung darf maximal die halbe Größe des Kontingents beanspruchen.  Installierte Anwendungen sind von der Größenbeschränkung für den Cache nicht betroffen und werden folglich nicht angerechnet.  Bei allen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen werden nur die aktuelle Version und die zuvor installierte Version im Cache gespeichert.  
  
 Standardmäßig stehen auf Clientcomputern 250 MB Speicher für online verfügbare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen zur Verfügung.  Datendateien werden in diesem Fall nicht einberechnet.  Systemadministratoren können dieses Kontingent für einen bestimmten Clientcomputer erweitern oder verringern, indem sie den Registrierungsschlüssel HKEY\_CURRENT\_USER\\Software\\Classes\\Software\\Microsoft\\Windows\\CurrentVersion\\Deployment\\OnlineAppQuotaInKB ändern. Hierbei handelt es sich um einen DWORD\-Wert, durch den die Cachegröße in KB ausgedrückt wird.  Um z. B. die Cachegröße auf 50 MB zu reduzieren, müsste dieser Wert in 51200 geändert werden.  
  
## Siehe auch  
 [Zugreifen auf lokale und Remotedaten in einer ClickOnce\-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)