---
title: Die experimentelle Instanz | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: c80c071866e46528fe7edd287e082df3af166973
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138924"
---
# <a name="the-experimental-instance"></a>Die experimentelle Instanz
Um der Visual Studio-Entwicklungsumgebung vor ungeprüfte Anwendungen schützen, die sie ändern können, bietet VSSDK eine experimentelle Fläche, die Sie verwenden können, um zu experimentieren. Sie neue Anwendungen mit Visual Studio wie gewohnt entwickeln, aber Sie ausführen, indem Sie mithilfe einer experimentellen Instanz.  
  
 Jede Anwendung, die ein VSIX-Paket wird die experimentelle Visual Studio-Instanz im Debugmodus gestartet.  
  
 Wenn Sie die experimentelle Instanz von Visual Studio außerhalb einer bestimmten Lösung beginnen möchten, führen Sie den folgenden Befehl an das Befehlsfenster:  
  
 "*\<Visual Studio-Installationspfad >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  Die experimentelle Instanz wird geschrieben, in der Registrierung unter dem `<version number>Exp` und `<version number>Exp_Config` Knoten. Befindet sich z. B. experimentelle Registrierungsstruktur Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` und `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Es wird empfohlen, dass Sie Ihre Erweiterung in der experimentellen Instanz ausführen, während Sie es entwickeln. Beim Bereitstellen der Erweiterung, der in der Entwicklungsinstanz ausgeführt wird. Weitere Informationen zum Registrieren von Anwendungen finden Sie unter [registrieren VSPackages](../extensibility/internals/registering-vspackages.md).