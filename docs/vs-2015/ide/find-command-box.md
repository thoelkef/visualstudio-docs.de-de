---
title: Feld „Suchen/Befehl“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b8bddc27eb4a59b65796c7837ae4561e5d56a5d5
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54801224"
---
# <a name="findcommand-box"></a>Suchen (Feld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Über das Feld **Find/Command** (Suchen/Befehl) können Sie nach Text suchen und Visual Studio-Befehle ausführen. Das Feld **Find/Command** (Suchen/Befehl) ist weiterhin als Steuerelement für die Symbolleiste verfügbar, wird standardmäßig aber nicht mehr angezeigt. Sie können das Feld **Find/Command** (Suchen/Befehl) einblenden, indem Sie in der Symbolleiste**Standard** auf **Schaltflächen hinzufügen oder entfernen** klicken und anschließend auf **Suchen** klicken.  
  
 Um einen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl auszuführen, leiten Sie ihn mit einem Größer-als-Zeichen (>) ein.  
  
 Das Feld **Suchen/Befehl** speichert die letzten 20 Eingaben und zeigt sie in einer Dropdownliste an. Mithilfe der Pfeiltasten kann in der Liste navigiert werden.  
  
 ![Feld „Suchen/Befehl“](../ide/media/findcommandbox.png "FindCommandFeld")  
Suchen (Feld)  
  
## <a name="searching-for-text"></a>Nach Text suchen  
 Wenn Sie Text im Feld **Suchen/Befehl** angeben und dann die EINGABETASTE drücken, durchsucht Visual Studio standardmäßig das aktuelle Dokument oder Toolfenster mithilfe der Optionen, die im Dialogfeld **In Dateien suchen** festgelegt wurden. Weitere Informationen finden Sie unter [Finding and Replacing Text](../ide/finding-and-replacing-text.md).  
  
## <a name="entering-commands"></a>Eingeben von Befehlen  
 Um über das Feld **Suchen/Befehl** einen einzelnen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl oder Alias auszugeben, anstatt nach Text zu suchen, geben Sie den gewünschten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl mit einem vorangestellten Größer-als-Zeichen (>) ein. Beispiel:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 Darüber hinaus können Sie auch das Befehlsfenster zum Eingeben und Ausführen von einzelnen oder mehreren Befehlen verwenden. Einige Befehle oder Aliase können eigenständig eingegeben und ausgeführt werden, für andere erfordert die Syntax die Angabe von Argumenten. Eine Liste mit Befehlen, die über Argumente verfügen, finden Sie unter [Visual Studio-Befehle](../ide/reference/visual-studio-commands.md).  
  
## <a name="escape-characters"></a>Escapezeichen  
 Ein Caretzeichen (^) in einer Befehlszeile bedeutet, dass das unmittelbar darauf folgende Zeichen literal und nicht als Steuerzeichen interpretiert wird. Dies ermöglicht das Einbetten von geraden Anführungszeichen ("), Leerzeichen, vorangestellten Schrägstrichen, Caretzeichen oder beliebigen anderen Literalzeichen in einen Parameter- oder Schalterwert, mit Ausnahme von Schalternamen. Ein auf ein Objekt angewendeter  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Die Funktionsweise des Caretzeichens ist unabhängig davon, ob es in Anführungszeichen eingeschlossen ist oder nicht. Wenn ein Caretzeichen das letzte Zeichen in einer Zeile ist, wird es ignoriert.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehlsfenster](../ide/reference/command-window.md)   
 [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)
