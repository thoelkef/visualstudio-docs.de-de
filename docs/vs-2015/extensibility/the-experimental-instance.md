---
title: Die experimentelle Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 212fc490c26ab66284cf7bdfa4e51946c817266d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220440"
---
# <a name="the-experimental-instance"></a>Die experimentelle Instanz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um Visual Studio-Entwicklungsumgebung nicht getestete Anwendungen zu schützen, die Sie sie ändern können, dient das VS SDK eines experimentellen, mit denen Sie experimentieren können. Sie können neue Anwendungen entwickeln, indem Sie mithilfe von Visual Studio wie gewohnt, aber Sie ausführen, indem Sie mithilfe dieser experimentellen Instanz.  
  
 Jede Anwendung, die ein VSIX-Paket wird die experimentelle Visual Studio-Instanz im Debugmodus gestartet.  
  
 Wenn Sie die experimentelle Instanz von Visual Studio außerhalb einer bestimmten Projektmappe starten möchten, führen Sie den folgenden Befehl im Befehlsfenster ein:  
  
 "*\<Visual Studio-Installationspfad >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  Die experimentelle Instanz richtet sich an der Registrierung unter dem `<version number>Exp` und `<version number>Exp_Config` Knoten. Beispielsweise ist der Visual Studio 2015 experimentelle Registrierung-Bereich  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` und `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Es wird empfohlen, dass Sie Ihre Erweiterung in der experimentellen Instanz ausführen, während Sie es entwickeln. Wenn Sie die Erweiterung bereitstellen, wird in der Entwicklungsinstanz ausgeführt. Weitere Informationen zum Registrieren von Anwendungen finden Sie unter [Registrieren von VSPackages](../extensibility/internals/registering-vspackages.md).

