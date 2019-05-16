---
title: Source Server Sicherheitswarnung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f8b122deab5dbdc30b129bce221a804f8c53aa3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699325"
---
# <a name="source-server-security-alert"></a>Quellserver-Sicherheitswarnung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie bei Verwendung von Source Server nur Symboldateien, die aus bekannten und vertrauenswürdigen Quellen stammen.  
  
 Diese Warnung wird angezeigt, wenn Sie die Quellserverunterstützung aktivieren. Quellserverbefehle sind in Debugsymboldateien (PDB-Dateien) eingebettet. Stellen Sie sicher, dass Sie wissen, woher die PDB-Dateien stammen.  
  
> [!IMPORTANT]
> Die folgenden potenziellen Sicherheitsrisiken müssen bei der Verwendung von Source Server berücksichtigt werden: Beliebige Befehle in PDB-Datei der Anwendung eingebettet werden kann, also stellen Sie sicher, dass Sie nur die Befehle hinzufügen, die Sie in der Datei srcsrv.ini ausführen möchten. Beim Versuch, einen nicht in der Datei srcsvr.ini enthaltenen Befehl auszuführen, wird ein Bestätigungsdialogfeld geöffnet. Weitere Informationen finden Sie unter [Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Wird keine Validierung für Befehlsparameter durchgeführt, seien Sie also bei vertrauenswürdigen Befehlen vorsichtig. Beispielsweise kann bei Vertrauenswürdigkeit für den Befehl cmd.exe ein böswilliger Benutzer Parameter angeben, die den Befehl gefährlich machen.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben von Symboldateien (PDB) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Debugger Security (Debuggersicherheit)](../debugger/debugger-security.md)   
 [Quellserver](https://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
