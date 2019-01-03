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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cacee26fb84774eb7f1043d940419561bc55ec36
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917371"
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