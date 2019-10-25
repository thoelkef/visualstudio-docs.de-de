---
title: '&#39;Neuerungen in der Quellcodeverwaltungs-Plug-in-API, Version 1,3 | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f45eeb3c57d5339b1e9fd66951dcbb60970e108
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721589"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>&#39;Neuerungen in der Quellcodeverwaltungs-Plug-in-API, Version 1,3
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

## <a name="see-also"></a>Siehe auch
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)