---
title: Befehl „Neues Element hinzufügen“ | Microsoft-Dokumentation
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
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f380a11440ed413871d2c80603148aa7cc77390
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520820"
---
# <a name="add-new-item-command"></a>Befehl "Neues Element hinzufügen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [neuen Befehl hinzufügen](https://docs.microsoft.com/visualstudio/ide/reference/add-new-item-command).  
  
  
Fügt der aktuellen Projektmappe ein neues Projektmappenelement wie eine HTM-, CSS-, TXT- oder Framesetdatei hinzu und öffnet dieses.  
  
## <a name="syntax"></a>Syntax  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumente  
 `filename`  
 Dies ist optional. Der Pfad und der Dateiname des Elements, das der Projektmappe hinzugefügt werden soll.  
  
## <a name="switches"></a>Schalter  
 /t: `templatename`  
 Dies ist optional. Gibt den Typ der zu erstellenden Datei an. Wenn kein Vorlagenname angegeben wird, wird standardmäßig eine Textdatei erstellt.  
  
 Die Argumentsyntax /t:`templatename` gibt die im Dialogfeld **Neues Projektmappenelement hinzufügen** gefundenen Informationen wieder. Es muss die vollständige Kategorie, gefolgt vom Dateityp, eingegeben werden; der Name der Kategorie wird mit einem umgekehrten Schrägstrich (`\`) vom Dateityp getrennt und die gesamte Zeichenfolge in Anführungszeichen eingeschlossen.  
  
 Um z.B. eine neue Textdatei zu erstellen, geben Sie für das Argument /t:`templatename` Folgendes ein:  
  
```  
/t:"General\Style Sheet"  
```  
  
 /e: `editorname`  
 Dies ist optional. Name des Editors, in dem die Datei geöffnet wird. Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.  
  
 Die Argumentsyntax /e:`editorname` verwendet die Editornamen wie im Dialogfeld **Öffnen mit** angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist.  
  
 Um ein Stylesheet im Quellcode-Editor zu öffnen, geben Sie für das Argument /e:`editorname` beispielsweise Folgendes ein:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird der aktuellen Projektmappe ein neues Projektmappenelement, MyHTMLpg, hinzugefügt.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)



