---
title: Befehl „Disassembly auflisten“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6834bc8f6c9bc3aacb95ae3705195fde32c4d6cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520807"
---
# <a name="list-disassembly-command"></a>Befehl "Disassemblierung auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Befehl "Disassemblierung auflisten"](https://docs.microsoft.com/visualstudio/ide/reference/list-disassembly-command).  
  
  
Startet den Debugprozess und ermöglicht es, die Behebung von Fehlern festzulegen.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>Schalter  
 Jeder Schalter kann sowohl mit der vollständigen als auch mit der Kurzform aufgerufen werden.  
  
 /count: `number` [oder] /c: `number` [oder] /length: `number` [oder] /l: `number`  
 Dies ist optional. Anzahl der anzuzeigenden Anweisungen. Der Standardwert ist 8.  
  
 /endaddress: `expression` [oder] /e: `expression`  
 Dies ist optional. Adresse, an der die Disassemblierung beendet wird.  
  
 /codebytes:`yes`|`no` [oder] /bytes:`yes`|`no` [oder] /b:`yes`|`no`  
 Dies ist optional. Gibt an, ob Codebytes angezeigt werden sollen. Der Standardwert ist `no`sein.  
  
 /source:`yes`|`no` [oder] /s:`yes`|`no`  
 Dies ist optional. Gibt an, ob Quellcode angezeigt werden soll. Der Standardwert ist `no`sein.  
  
 /symbolnames:`yes`|`no` [oder] /names:`yes`|`no` [oder] /n:`yes`|`no`  
 Dies ist optional. Gibt an, ob Symbolnamen angezeigt werden sollen. Der Standardwert ist `yes`sein.  
  
 [/linenumbers:`yes`|`no`]  
 Dies ist optional. Ermöglicht das Anzeigen von dem Quellcode zugeordneten Zeilennummern. Der Schalter „/source“ muss den Wert `yes` haben, um den Schalter „/linenumbers“ zu verwenden.  
  
## <a name="example"></a>Beispiel  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehl „Aufrufliste auflisten“](../../ide/reference/list-call-stack-command.md)   
 [Befehl „Threads auflisten“](../../ide/reference/list-threads-command.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)



