---
title: Was&#39;Neues in der Quelle steuern-Plug-in-API-Version 1.3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b61e56fcef8bbbe8e9f36a39580eae14ad582d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856717"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Was&#39;Neues in der Quelle steuern-Plug-in-API-Version 1.3
Die Source-Plug-in-API Version 1.3 führt die folgenden neuen Funktionen, um erweiterte Kontrolle zu erhalten.

## <a name="changes"></a>Änderungen
 Die folgenden Funktionen sind neu in der Quelle-Plug-in-API Version 1.3:

|Funktion|Übersicht|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Zusätzliche Funktionsbits gemeldet werden können|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Ermöglicht die Untersuchung von Dateien, die neuere Versionen in der Datenbank der Versionskontrolle als auf dem lokalen Datenträger aufweisen|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Ermöglicht die Prüfung des Zustands von Namensänderungen (umbenennen, Hinzufügungen und löschungen) angegebenen Dateien|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Ermöglicht die Untersuchung von Verzeichnissen und Dateien in der Datenbank der Versionskontrolle|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Fügt eine angegebene Liste von Dateien aus der Datenbank der Versionskontrolle für das aktuelle Projekt|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Führt eine automatische "Get" der angegebenen Dateien (keine Benutzeroberfläche wird angezeigt.)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Ermöglicht den Zugriff auf die benutzerspezifischen Optionen|

## <a name="see-also"></a>Siehe auch
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)