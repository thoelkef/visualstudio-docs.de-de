---
title: Befehl „Symbolpfad“ | Microsoft-Dokumentation
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
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b21a745177722160b100d0bbad770c3a74c40ca3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511067"
---
# <a name="symbol-path-command"></a>Befehl "Symbolpfad"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Befehl "Symbolpfad"](https://docs.microsoft.com/visualstudio/ide/reference/symbol-path-command).  
  
  
Legt die Liste mit Verzeichnissen fest, in denen der Debugger nach Symbolen sucht.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Argumente  
 `pathname`  
 Dies ist optional. Ein durch Semikolons getrennte Liste der Pfade, in denen der Debugger nach Symbolen sucht.  
  
## <a name="remarks"></a>Hinweise  
 Wenn kein `pathname` angegeben wird, werden von dem Befehl die aktuellen Symbolpfade aufgelistet.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden der Liste mit Symbolverzeichnissen zwei Pfade hinzugefügt.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird eine durch Semikolons getrennte Liste der aktuellen Symbolpfade angezeigt.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)



