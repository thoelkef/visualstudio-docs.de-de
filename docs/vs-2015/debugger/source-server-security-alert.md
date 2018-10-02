---
title: Source Server Sicherheitswarnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b971a05f9cd8873a1dbac3cafe6865ffce238868
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512692"
---
# <a name="source-server-security-alert"></a>Quellserver-Sicherheitswarnung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Source Server Sicherheitswarnung](https://docs.microsoft.com/visualstudio/debugger/source-server-security-alert).  
  
Verwenden Sie bei Verwendung von Source Server nur Symboldateien, die aus bekannten und vertrauenswürdigen Quellen stammen.  
  
 Diese Warnung wird angezeigt, wenn Sie die Quellserverunterstützung aktivieren. Quellserverbefehle sind in Debugsymboldateien (PDB-Dateien) eingebettet. Stellen Sie sicher, dass Sie wissen, woher die PDB-Dateien stammen.  
  
> [!IMPORTANT]
>  Folgende Sicherheitsrisiken müssen bei Verwendung des Quellservers berücksichtigt werden: In der PDB-Datei der Anwendung können beliebige Befehle eingebettet sein. Deshalb sollten Sie sicherstellen, dass Sie der Datei srcsrv.ini nur die Befehle hinzufügen, die ausführt werden dürfen. Beim Versuch, einen nicht in der Datei srcsvr.ini enthaltenen Befehl auszuführen, wird ein Bestätigungsdialogfeld geöffnet. Weitere Informationen finden Sie unter [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Wird keine Validierung für Befehlsparameter durchgeführt, seien Sie also bei vertrauenswürdigen Befehlen vorsichtig. Beispielsweise kann bei Vertrauenswürdigkeit für den Befehl cmd.exe ein böswilliger Benutzer Parameter angeben, die den Befehl gefährlich machen.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Quellserver](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)



