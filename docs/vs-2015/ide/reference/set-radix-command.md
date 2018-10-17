---
title: Befehl „Wurzel setzen“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f0df00cf4c1d1264692be5ab5313eb9f03920b3c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296126"
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



