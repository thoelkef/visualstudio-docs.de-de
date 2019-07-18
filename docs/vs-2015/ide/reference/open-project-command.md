---
title: Befehl „Projekt öffnen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: e2e945eb2faa492f576a0fd0a15fc0bd0e9b208e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199041"
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
  
## <a name="remarks"></a>Anmerkungen  
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
