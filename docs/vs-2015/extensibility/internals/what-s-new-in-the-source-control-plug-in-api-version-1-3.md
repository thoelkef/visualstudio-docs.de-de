---
title: Neuerungen in der API-Version 1,3 für die Quellcodeverwaltungs-Plug-ins&#39;Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5333a5b44e9c990843e66da357578e4a90d210
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200928"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Neuerungen in der API-Version 1,3 der Quellcodeverwaltungs-Plug-ins&#39;
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die API-Version 1,3 der Quellcodeverwaltungs-Plug-in führt die folgenden neuen Funktionen ein, um erweiterte Steuerungsmöglichkeiten bereitzustellen.  
  
## <a name="changes"></a>Änderungen  
 Die folgenden Funktionen sind neu in der API-Version 1,3 der Quellcodeverwaltungs-Plug-in:  
  
|Funktion|Übersicht|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Ermöglicht das melden zusätzlicher Funktionsbits.|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Ermöglicht die Untersuchung von Dateien, die neuere Versionen in der Versionskontrolldatenbank aufweisen als auf dem lokalen Datenträger.|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Ermöglicht die Untersuchung des Zustands von Namensänderungen (umbenennen, Hinzufügungen und Löschungen) für angegebene Dateien.|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Ermöglicht die Untersuchung von Verzeichnissen und Dateien in der Versions kontrolldatenbank.|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Fügt dem aktuellen Projekt eine angegebene Liste von Dateien aus der Versions kontrolldatenbank hinzu.|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Führt eine automatische "Get"-Angabe der angegebenen Dateien aus (es wird keine Benutzeroberfläche angezeigt)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Ermöglicht den Zugriff auf benutzerspezifische Optionen|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einstieg](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
