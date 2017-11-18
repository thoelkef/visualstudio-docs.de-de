---
title: Die experimentelle Instanz | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2de242ed974716b0ba00918d30bc2679a36420fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="the-experimental-instance"></a>Die experimentelle Instanz
Um der Visual Studio-Entwicklungsumgebung vor ungeprüfte Anwendungen schützen, die sie ändern können, bietet VSSDK eine experimentelle Fläche, die Sie verwenden können, um zu experimentieren. Sie neue Anwendungen mit Visual Studio wie gewohnt entwickeln, aber Sie ausführen, indem Sie mithilfe einer experimentellen Instanz.  
  
 Jede Anwendung, die ein VSIX-Paket wird die experimentelle Visual Studio-Instanz im Debugmodus gestartet.  
  
 Wenn Sie die experimentelle Instanz von Visual Studio außerhalb einer bestimmten Lösung beginnen möchten, führen Sie den folgenden Befehl an das Befehlsfenster:  
  
 "*\<Visual Studio-Installationspfad >*\Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  Die experimentelle Instanz wird geschrieben, in der Registrierung unter dem `<version number>Exp` und `<version number>Exp_Config` Knoten. Befindet sich z. B. experimentelle Registrierungsstruktur Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` und `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Es wird empfohlen, dass Sie Ihre Erweiterung in der experimentellen Instanz ausführen, während Sie es entwickeln. Beim Bereitstellen der Erweiterung, der in der Entwicklungsinstanz ausgeführt wird. Weitere Informationen zum Registrieren von Anwendungen finden Sie unter [registrieren VSPackages](../extensibility/internals/registering-vspackages.md).