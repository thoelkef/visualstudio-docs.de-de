---
title: Was&#39;s in der Quelle steuern-Plug-in-API-Version 1.3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abeb2a0a936a5d706e2e3744e9dd0f4e3123bdbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31145008"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Was&#39;s in der Quelle steuern-Plug-in-API-Version 1.3
Die Datenquellen-Steuerelement-Plug-in-API Version 1.3 führt die folgenden neuen Funktionen, um erweiterte Kontrolle zu erhalten.  
  
## <a name="changes"></a>Änderungen  
 Die folgenden Funktionen sind neu in der Quelle Steuerelement-Plug-in-API Version 1.3:  
  
|Funktion|Übersicht|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Zusätzliche Funktionsbits gemeldet werden können|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Ermöglicht die Untersuchung von Dateien mit neueren Versionen in der Datenbank der Versionskontrolle als auf dem lokalen Datenträger|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Ermöglicht die Prüfung des Zustands von Namensänderungen (umbenennen, hinzufügen oder löschen) angegebenen Dateien|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Ermöglicht die Analyse von Verzeichnissen und Dateien in der Datenbank der Versionskontrolle|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Fügt eine angegebene Liste von Dateien aus der Datenbank der Versionskontrolle für das aktuelle Projekt|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Führt eine unbeaufsichtigte "Get" der angegebenen Dateien (es wird keine Benutzeroberfläche angezeigt)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Ermöglicht den Zugriff auf benutzerspezifische-Optionen|  
  
## <a name="see-also"></a>Siehe auch  
 [Getting Started (Erste Schritte)](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)