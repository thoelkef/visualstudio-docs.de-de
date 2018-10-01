---
title: Feld „Suchen/Befehl“ | Microsoft-Dokumentation
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
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22ced396f8a18cf2a665ed7a1ba1016b16e44c8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511981"
---
# <a name="findcommand-box"></a>Suchen (Feld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Such-/ Befehlsfeld](https://docs.microsoft.com/visualstudio/ide/find-command-box).  
  
Über das Feld **Find/Command** (Suchen/Befehl) können Sie nach Text suchen und Visual Studio-Befehle ausführen. Das Feld **Find/Command** (Suchen/Befehl) ist weiterhin als Steuerelement für die Symbolleiste verfügbar, wird standardmäßig aber nicht mehr angezeigt. Sie können das Feld **Find/Command** (Suchen/Befehl) einblenden, indem Sie in der Symbolleiste**Standard** auf **Schaltflächen hinzufügen oder entfernen** klicken und anschließend auf **Suchen** klicken.  
  
 Um einen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl auszuführen, leiten Sie ihn mit einem Größer-als-Zeichen (>) ein.  
  
 Das Feld **Suchen/Befehl** speichert die letzten 20 Eingaben und zeigt sie in einer Dropdownliste an. Mithilfe der Pfeiltasten kann in der Liste navigiert werden.  
  
 ![Feld „Suchen/Befehl“](../ide/media/findcommandbox.png "FindCommandFeld")  
Suchen (Feld)  
  
## <a name="searching-for-text"></a>Nach Text suchen  
 Wenn Sie Text im Feld **Suchen/Befehl** angeben und dann die EINGABETASTE drücken, durchsucht Visual Studio standardmäßig das aktuelle Dokument oder Toolfenster mithilfe der Optionen, die im Dialogfeld **In Dateien suchen** festgelegt wurden. Weitere Informationen finden Sie unter [Finding and Replacing Text](../ide/finding-and-replacing-text.md).  
  
## <a name="entering-commands"></a>Eingeben von Befehlen  
 Um über das Feld **Suchen/Befehl** einen einzelnen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl oder Alias auszugeben, anstatt nach Text zu suchen, geben Sie den gewünschten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl mit einem vorangestellten Größer-als-Zeichen (>) ein. Zum Beispiel:  
  
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



