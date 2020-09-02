---
title: Die experimentelle Instanz | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699040"
---
# <a name="the-experimental-instance"></a>Die experimentelle Instanz
Um Ihre Visual Studio-Entwicklungsumgebung vor nicht getesteten Anwendungen zu schützen, die Sie möglicherweise ändern, bietet das VSSDK einen experimentellen Bereich, mit dem Sie experimentieren können. Sie entwickeln neue Anwendungen wie gewohnt mithilfe von Visual Studio, führen Sie jedoch mit dieser experimentellen Instanz aus.

 Jede Anwendung, die über ein VSIX-Paket verfügt, öffnet die experimentelle Instanz von Visual Studio im Debugmodus.

 Wenn Sie die experimentelle Instanz von Visual Studio außerhalb einer bestimmten Projekt Mappe starten möchten, führen Sie im Befehlsfenster den folgenden Befehl aus:

 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe"/RootSuffix Exp

> [!NOTE]
> Die experimentelle Instanz wird in die Registrierung unter den `<version number>Exp` Knoten und geschrieben `<version number>Exp_Config` . Der experimentelle Registrierungsbereich von Visual Studio 2015 lautet z. b.
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` und `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Es wird empfohlen, dass Sie die Erweiterung in der experimentellen Instanz ausführen, während Sie Sie entwickeln. Wenn Sie die Erweiterung bereitstellen, wird Sie in der Entwicklungs Instanz ausgeführt. Weitere Informationen zum Registrieren von Anwendungen finden Sie unter [Registrieren von VSPackages](../extensibility/internals/registering-vspackages.md).
