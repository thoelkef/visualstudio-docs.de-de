---
title: Die experimentelle Instanz | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c4aa7e8e74ccb8f31dc2320192cf088b5391678
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685117"
---
# <a name="the-experimental-instance"></a>Die experimentelle Instanz
Um Visual Studio-Entwicklungsumgebung nicht getestete Anwendungen zu schützen, die Sie sie ändern können, dient das VS SDK eines experimentellen, mit denen Sie experimentieren können. Sie können neue Anwendungen entwickeln, indem Sie mithilfe von Visual Studio wie gewohnt, aber Sie ausführen, indem Sie mithilfe dieser experimentellen Instanz.

 Jede Anwendung, die ein VSIX-Paket wird die experimentelle Visual Studio-Instanz im Debugmodus gestartet.

 Wenn Sie die experimentelle Instanz von Visual Studio außerhalb einer bestimmten Projektmappe starten möchten, führen Sie den folgenden Befehl im Befehlsfenster ein:

 "*\<Visual Studio-Installationspfad >* \Common7\IDE\devenv.exe" RootSuffix Exp

> [!NOTE]
>  Die experimentelle Instanz richtet sich an der Registrierung unter dem `<version number>Exp` und `<version number>Exp_Config` Knoten. Beispielsweise ist der Visual Studio 2015 experimentelle Registrierung-Bereich
>
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` und `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Es wird empfohlen, dass Sie Ihre Erweiterung in der experimentellen Instanz ausführen, während Sie es entwickeln. Wenn Sie die Erweiterung bereitstellen, wird in der Entwicklungsinstanz ausgeführt. Weitere Informationen zum Registrieren von Anwendungen finden Sie unter [Registrieren von VSPackages](../extensibility/internals/registering-vspackages.md).