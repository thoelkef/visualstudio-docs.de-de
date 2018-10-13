---
title: Befehl „Projekt öffnen“ | Microsoft-Dokumentation
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
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b25ee0e6ba4dfa5c29d5a009087afb55509d0c08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263914"
---
# <a name="open-project-command"></a>Befehl "Projekt öffnen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Öffnet ein vorhandenes Projekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Argumente  
 `filename`  
 Erforderlich. Der vollständige Pfad und Dateiname der Projektdatei, die Sie öffnen wollen.  
  
 Die Syntax für das Argument `filename` erfordert, dass Pfade, die Leerzeichen enthalten, in Anführungszeichen gesetzt werden.  
  
## <a name="remarks"></a>Hinweise  
 Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.  
  
 Dieser Befehl ist während des Debuggens nicht verfügbar.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Projekt, Test1, geöffnet.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



