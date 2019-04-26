---
title: Befehl „Vorhandenes Element hinzufügen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8ad1ab33de1aa0d25f7beff0dac43ebedbf0f6b4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539944"
---
# <a name="add-existing-item-command"></a>Befehl "Vorhandenes Element hinzufügen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Fügt der aktuellen Projektmappe eine vorhandene Datei hinzu und öffnet diese.  
  
## <a name="syntax"></a>Syntax  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumente  
 `filename`  
 Erforderlich. Der vollständige Pfad und der Dateiname des Elements, das einschließlich der Erweiterung der aktuellen Projektmappe hinzugefügt werden sollen. Wenn der Dateipfad oder Dateiname Leerzeichen enthalten, schließen Sie den vollständigen Pfad in Anführungszeichen ein.  
  
## <a name="switches"></a>Schalter  
 /e: `editorname`  
 Dies ist optional. Der Name des Editors, in dem die Datei geöffnet wird. Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.  
  
 Die Argumentsyntax /e:`editorname` verwendet die Editornamen wie im Dialogfeld **Öffnen mit** angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist. Um ein Stylesheet im Quellcode-Editor zu öffnen, geben Sie für das Argument /e:`editorname` beispielsweise Folgendes ein:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Anmerkungen  
 Bei der automatischen Vervollständigung wird während der Eingabe versucht, den richtigen Pfad und Dateinamen zu finden.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel fügt die Datei „Form1.frm“ der aktuellen Projektmappe zu.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
