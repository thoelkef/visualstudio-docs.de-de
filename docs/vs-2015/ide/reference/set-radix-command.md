---
title: Befehl „Wurzel setzen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c315ccb0bc7404ddbaa303430644b404a570e016
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798089"
---
# <a name="set-radix-command"></a>Befehl "Wurzel setzen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Legt die zum Anzeigen von ganzzahligen Werten verwendete numerische Basis fest bzw. gibt sie zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Argumente  
 `10` oder `16` oder `hex` oder `dec`  
 Dies ist optional. Legt „dezimal“ (10 bzw. dec) oder „hexadezimal“ (16 bzw. hex) als Format fest. Wird ein Argument weggelassen, wird der aktuelle Wert der Wurzel zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die Umgebung zum Anzeigen ganzzahliger Werte im Hexadezimalformat konfiguriert.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
