---
title: Befehl „Disassembly auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ff87add99fb618eaa45d6f9a71a68d82149884e3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753394"
---
# <a name="list-disassembly-command"></a>Befehl "Disassemblierung auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
