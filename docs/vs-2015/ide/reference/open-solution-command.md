---
title: Befehl „Projektmappe öffnen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 298609aa37557eebc52dce7ca6eada2f98f2096d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54759985"
---
# <a name="open-solution-command"></a>Befehl "Projektmappe öffnen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Öffnet eine vorhandene Projektmappe und schließt alle anderen geöffneten Projektmappen.  
  
## <a name="syntax"></a>Syntax  
  
```  
File.OpenSolution filename  
```  
  
## <a name="arguments"></a>Argumente  
 `Filename`  
 Erforderlich. Der vollständige Pfad und Dateiname der zu öffnenden Projektmappe.  
  
 Die Syntax für das Argument `filename` erfordert, dass Pfade, die Leerzeichen enthalten, in Anführungszeichen gesetzt werden.  
  
## <a name="remarks"></a>Anmerkungen  
 Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird die Projektmappe „Test1.sln“ geöffnet.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
