---
title: Die experimentelle Instanz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699040"
---
# <a name="the-experimental-instance"></a>Die experimentelle Instanz
Um Ihre Visual Studio-Entwicklungsumgebung vor nicht getesteten Anwendungen zu schützen, die sie ändern können, bietet das VSSDK einen experimentellen Raum, den Sie zum Experimentieren verwenden können. Sie entwickeln neue Anwendungen, indem Sie Visual Studio wie gewohnt verwenden, aber Sie führen sie mithilfe dieser experimentellen Instanz aus.

 Jede Anwendung mit einem VSIX-Paket startet die experimentelle Visual Studio-Instanz im Debugmodus.

 Wenn Sie die experimentelle Instanz von Visual Studio außerhalb einer bestimmten Lösung starten möchten, führen Sie den folgenden Befehl im Befehlsfenster aus:

 "*\<Visual Studio-Installationspfad>*"Common7"IDE-devenv.exe" /RootSuffix Exp

> [!NOTE]
> Die experimentelle Instanz wird unter `<version number>Exp` dem `<version number>Exp_Config` und in die Registrierung geschrieben. Der experimentelle Registrierungsbereich von Visual Studio 2015 ist z. B.
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` und `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Es wird empfohlen, die Erweiterung in der experimentellen Instanz auszuführen, während Sie sie entwickeln. Wenn Sie die Erweiterung bereitstellen, wird sie in der Entwicklungsinstanz ausgeführt. Weitere Informationen zum Registrieren von Anwendungen finden Sie unter [Registrieren von VSPackages](../extensibility/internals/registering-vspackages.md).
