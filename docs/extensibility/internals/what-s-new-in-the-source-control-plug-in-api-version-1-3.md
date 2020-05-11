---
title: Was&#39;ist neu in der Quellcodeverwaltung Plug-in-API Version 1.3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703362"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Was&#39;ist neu in der Quellcodeverwaltung Plug-in-API Version 1.3
Die Quellcodeverwaltungs-Plug-In-API-Version 1.3 führt die folgenden neuen Funktionen ein, um eine erweiterte Steuerung bereitzustellen.

## <a name="changes"></a>Änderungen
 Die folgenden Funktionen sind neu in der Quellcodeverwaltung Plug-in-API Version 1.3:

|Funktion|Übersicht|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Ermöglicht die Gemeldetkeit zusätzlicher Funktionsbits|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Ermöglicht die Prüfung von Dateien, die neuere Versionen in der Versionssteuerungsdatenbank als auf dem lokalen Datenträger haben|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Ermöglicht die Prüfung des Status von Namensänderungen (Umbenennungen, Ergänzungen und Löschungen) für bestimmte Dateien|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Ermöglicht die Prüfung von Verzeichnissen und Dateien in der Versionskontrolldatenbank|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Fügt dem aktuellen Projekt eine angegebene Liste von Dateien aus der Versionskontrolldatenbank hinzu|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Führt ein stilles "Get" der angegebenen Dateien aus (es wird keine Benutzeroberfläche angezeigt)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Ermöglicht den Zugriff auf benutzerspezifische Optionen|

## <a name="see-also"></a>Weitere Informationen
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
