---
title: Eliminierung von SAK-Dateien | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708504"
---
# <a name="elimination-of-sak-files"></a>Eliminierung von SAK-Dateien
In der Quellcodeverwaltungs-Plug-In-API 1.2 wurden die *Dateien "SAK"* durch Funktionsflags und neue Funktionen ersetzt, die erkennen, ob ein Quellcodeverwaltungs-Plug-In die *MSSCCPRJ-Datei* und freigegebene Auschecken unterstützt.

## <a name="sak-files"></a>SAK-Dateien
Visual Studio .NET 2003 erstellte temporäre Dateien mit dem Präfix *"SAK*" . Diese Dateien werden verwendet, um zu bestimmen, ob ein Quellcodeverwaltungs-Plug-In unterstützt:

- Die *MsSCCPRJ.SCC-Datei.*

- Mehrere (gemeinsame) Checkouts.

Bei Plug-Ins, die erweiterte Funktionen unterstützen, die in der Quellcodeverwaltungs-Plug-In-API 1.2 bereitgestellt werden, kann die IDE diese Funktionen erkennen, ohne die temporären Dateien mithilfe neuer Funktionen, Flags und Funktionen zu erstellen, die in den folgenden Abschnitten beschrieben werden.

## <a name="new-capability-flags"></a>Neue Funktionsflags
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Neue Funktionen
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Wenn ein Quellcodeverwaltungs-Plug-In mehrere (gemeinsame) Auscheckungen `SCC_CAP_MULTICHECKOUT` unterstützt, deklariert `SccIsMultiCheckOutEnabled` es die Funktion und implementiert die Funktion. Diese Funktion wird aufgerufen, wenn ein Auscheckvorgang für eines der von der Quelle kontrollierten Projekte auftritt.

 Wenn ein Quellcodeverwaltungs-Plug-In die Erstellung und Verwendung einer *MSSCCPRJ.SCC-Datei* unterstützt, deklariert es die `SCC_CAP_SCCFILE` Funktion und implementiert die [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md). Diese Funktion wird mit einer Liste von Dateien aufgerufen. Die Funktion `TRUE' or 'FALSE` gibt für jede Datei zurück, um anzugeben, ob Visual Studio eine *MSSCCPRJ.SCC-Datei* dafür verwenden soll. Wenn das Quellcodeverwaltungs-Plug-In diese neuen Funktionen und Funktionen nicht unterstützt, kann es den folgenden Registrierungsschlüssel verwenden, um die Erstellung dieser Dateien zu deaktivieren:

 **[HKEY_CURRENT_USER-Software-, Microsoft-VisualStudio-8.0-SourceControl] DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*

> [!NOTE]
> Wenn dieser Registrierungsschlüssel auf *dword:00000000*festgelegt ist, entspricht er dem Nichtexistenten des Schlüssels, und Visual Studio versucht weiterhin, die temporären Dateien zu erstellen. Wenn der Registrierungsschlüssel jedoch auf *dword:00000001*festgelegt ist, versucht Visual Studio nicht, die temporären Dateien zu erstellen. Stattdessen wird davon ausgegangen, dass das Quellcodeverwaltungs-Plug-In die *MSSCCPRJ.SCC-Datei* nicht unterstützt und keine freigegebenen Auschecken unterstützt.

## <a name="see-also"></a>Weitere Informationen
- [Neuerungen in der Quellcodeverwaltungs-Plug-In-API Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
