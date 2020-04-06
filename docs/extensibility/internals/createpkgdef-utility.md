---
title: CreatePkgDef-Dienstprogramm | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709164"
---
# <a name="createpkgdef-utility"></a>Dienstprogramm CreatePkgDef
Nimmt eine DLL-Datei für eine Visual Studio-Erweiterung als Parameter und erstellt eine *.pkgdef-Datei,* um die *DLL-Datei* zu begleiten. Die *.pkgdef-Datei* enthält alle Informationen, die andernfalls in die Systemregistrierung geschrieben würden, wenn die Erweiterung installiert wird.

> [!NOTE]
> Die meisten Projektvorlagen, die im Visual Studio SDK enthalten sind, erstellen *automatisch .pkgdef-Dateien* als Teil des Buildprozesses. Dieses Dokument ist für diejenigen gedacht, die Pakete manuell erstellen oder vorhandene Pakete konvertieren möchten, um *.pkgdef-Bereitstellung* zu verwenden.

## <a name="syntax"></a>Syntax

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argumente
**/out=&lt;Dateiname&gt;**\
Erforderlich. Legt den Namen der *.pkgdef-Ausgabedatei* auf FileName &lt;&gt;fest.

**/codebase**\
Optional. Erzwingt die Registrierung beim **CodeBase-Dienstprogramm.**

**/Assembly**\
Erzwingt die **Assembly** Registrierung beim Assembly-Dienstprogramm.

**&lt;Assemblypath&gt;**\
Der Pfad der *DLL-Datei,* aus der Sie die *.pkgdef*generieren möchten.

## <a name="remarks"></a>Bemerkungen
Die Erweiterungsbereitstellung mithilfe von *.pkgdef-Dateien* ersetzt die Registrierungsanforderungen früherer Versionen von Visual Studio.

::: moniker range=">=vs-2019"

Die *.pkgdef-Dateien* müssen an einem der folgenden Speicherorte installiert werden:

- *%localappdata%-Microsoft-Visual Studio-16,0-Erweiterungen\\*

- *%vsinstalldir%-Common7-IDE-Erweiterungen\\*

Wenn der Installationsordner *%localappdata%-Microsoft-Visual Studio-16.0-Erweiterungen\\*ist, wird die Erweiterung von Visual Studio erkannt, ist jedoch standardmäßig deaktiviert. Der Benutzer kann die Erweiterung mithilfe von **Erweiterungen verwalten**aktivieren.

Wenn der Installationsordner *%vsinstalldir%-Common7-IDE-Extensions\\*ist, ist die Erweiterung standardmäßig aktiviert.

> [!NOTE]
> Das Tool **Erweiterungen verwalten** kann nicht für den Zugriff auf eine Erweiterung verwendet werden, es sei denn, es wird als Teil eines VSIX-Pakets installiert.

::: moniker-end

::: moniker range="vs-2017"

Die *.pkgdef-Dateien* müssen an einem der folgenden Speicherorte installiert werden:

- *%localappdata%-Microsoft-Visual Studio-15,0-Erweiterungen\\*

- *%vsinstalldir%-Common7-IDE-Erweiterungen\\*

Wenn der Installationsordner *%localappdata%-Microsoft-Visual Studio-Erweiterungen\\*ist, wird die Erweiterung von Visual Studio erkannt, aber standardmäßig deaktiviert. Der Benutzer kann die Erweiterung mithilfe von **Erweiterungen und Updates**aktivieren.

Wenn der Installationsordner *%vsinstalldir%-Common7-IDE-Extensions\\*ist, ist die Erweiterung standardmäßig aktiviert.

> [!NOTE]
> Das Tool **"Erweiterungen und Updates"** kann nur für den Zugriff auf eine Erweiterung verwendet werden, wenn sie als Teil eines VSIX-Pakets installiert ist.

::: moniker-end

## <a name="see-also"></a>Weitere Informationen
- [CreateExpInstance-Dienstprogramm](../../extensibility/internals/createexpinstance-utility.md)
