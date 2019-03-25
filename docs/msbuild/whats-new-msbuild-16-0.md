---
title: Neuerungen in MSBuild 16.0 | Microsoft-Dokumentation
ms.date: 03/11/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9fb23c8a48493056c9a37f510cefea3cc3374095
ms.sourcegitcommit: 4c7a0c2d712eb24609216577a793e912a6083eaf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "57987111"
---
# <a name="whats-new-in-msbuild-160"></a>Neuerungen in MSBuild 16.0

In diesem Artikel werden die aktualisierten Funktionen und Eigenschaften in MSBuild 16.0 beschrieben. Die detaillierten Versionshinweise (Entwurf) finden Sie unter [MSBuild 16.0](https://gist.github.com/rainersigwald/009627466f03964d0028e16fda633d9c).

## <a name="changed-path"></a>Geänderter Pfad

 MSBuild wird im Ordner *\Current* der jeweiligen Version von Visual Studio installiert. Beispiel: *C:\Program Files (x86)\Microsoft Visual Studio\Current\Enterprise\MSBuild*. Sie können MSBuild auch mit dem folgenden PowerShell-Modul suchen: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Geänderte Eigenschaften

 Die folgenden MSBuild-Eigenschaften wurden aufgrund der neuen Versionsnummer aktualisiert.

- `MSBuildToolsVersion` für diese Version der Tools ist „Current“. Die Assembly-Version ist 15.1.0.0 und entspricht somit der von Visual Studio 2017.

- `VisualStudioVersion` für diese Version der Tools ist „16.0“.

## <a name="updates"></a>Updates

MSBuild (und Visual Studio) zielt jetzt auf .NET Framework 4.7.2 ab. Wenn Sie die neuen MSBuild-API-Funktionen verwenden möchten, müssen Sie ebenfalls ein Upgrade Ihrer Assembly durchführen, wobei vorhandener Code aber weiterhin funktionsfähig bleibt.

## <a name="see-also"></a>Siehe auch
- [MSBuild](../msbuild/msbuild.md)
