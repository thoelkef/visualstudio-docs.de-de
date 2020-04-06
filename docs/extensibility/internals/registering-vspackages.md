---
title: Registrieren von VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b40793a5ab317b6a467e55df13302f19cec82640
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705743"
---
# <a name="registering-vspackages"></a>Registrieren von VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verwendet .pkgdef-Dateien, um ein VSPackage zu beschreiben und zu finden. Eine .pkgdef-Datei enthält alle Registrierungsinformationen, die andernfalls der Systemregistrierung hinzugefügt würden. Verwaltete VSPackages werden registriert, indem Attribute zum Quellcode hinzugefügt und dann das [CreatePkgDef-Dienstprogramm](../../extensibility/internals/createpkgdef-utility.md) auf der resultierenden Assembly ausgeführt wird, um eine .pkgdef-Datei zu generieren.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Angeben des VSPackage-Dateispeicherorts für die VS Shell](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Beschreibt den Ladepfad für VSPackages.

- [Registrieren und Aufheben der Registrierung von VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Erläutert, wie ein VSPackage registriert wird.
