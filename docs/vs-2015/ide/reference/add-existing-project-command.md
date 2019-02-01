---
title: Befehl „Vorhandenes Projekt hinzufügen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7523db6598a32c76944c22bfdabe56ee288c6b43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771081"
---
# <a name="add-existing-project-command"></a>Befehl "Vorhandenes Projekt hinzufügen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Fügt der aktuellen Projektmappe ein vorhandenes Projekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Argumente  
 `filename`  
 Dies ist optional. Der vollständige Pfad und der Projektname des Projekts mit Erweiterung, die der Projektmappe hinzugefügt werden sollen.  
  
 Wenn das `filename`-Argument Leerzeichen enthält, muss es in Anführungszeichen stehen.  
  
 Wenn kein Dateiname angegeben ist, öffnet der Befehl das Dialogfeld „Datei“, damit der Benutzer ein Projekt auswählen kann.  
  
## <a name="remarks"></a>Hinweise  
 Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Projekt, TestProject1, der aktuellen Projektmappe hinzugefügt.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
