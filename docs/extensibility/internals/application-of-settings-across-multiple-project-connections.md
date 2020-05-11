---
title: Anwendung von Einstellungen über mehrere Projektverbindungen hinweg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710064"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Anwendung von Einstellungen über mehrere Projektverbindungen hinweg
Ein Quellcodeverwaltungs-Plug-In, das mit der Quellcodeverwaltungs-Plug-In-API Version 1.2 erstellt wurde, kann einen Batchvorgang verwenden, um denselben Quellcodeverwaltungsvorgang über mehrere Projekte oder mehrere Verbindungskontexte auszuführen. Batches können verwendet werden, um redundante Dialogfelder pro Projekt aus der Benutzererfahrung zu entfernen.

 Wenn ein Benutzer mehrere Elemente auswählt, die zu mehr als einer Verbindung in einem Quellcodeverwaltungs-Plug-In gehören, das mit der Quellcodeverwaltungs-Plug-In-API Version 1.1 erstellt wurde (z. B. zwei Webprojekte auf verschiedenen Dateifreigabecomputern), und diese auscheckt, wird das gleiche Dialogfeld wiederholt angezeigt. Dieses Szenario tritt auch dann auf, wenn der Benutzer im Dialogfeld auf das Kontrollkästchen Auf **Alle anwenden** klickt, da die IDE ihren Status für jeden Verbindungskontext zurücksetzt.

## <a name="new-capability-flag"></a>Neues Fähigkeitsflag
 Die `SccBeginBatch` Funktion `SCC_CAP_BATCH` legt das Flag so fest, dass ein Stapelvorgang ausgeführt wird.

## <a name="new-functions"></a>Neue Funktionen
Die folgenden neuen Funktionen unterstützen den Batch-Vorgang:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

Die `SCCBeginBatch` Funktion startet eine Gruppe von Quellcodeverwaltungsvorgängen. Die `SccEndBatch` Funktion schließt die Gruppe. Die Gruppen dürfen nicht geschachtelt werden.

## <a name="see-also"></a>Weitere Informationen
- [Neuerungen in der Quellcodeverwaltungs-Plug-In-API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
