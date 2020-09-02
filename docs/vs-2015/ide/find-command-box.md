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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b7c5f9c19573a04b1d9a8d7b8c6e9450aef9bc44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645732"
---
# <a name="findcommand-box"></a>Suchen (Feld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Über das Feld **Find/Command** (Suchen/Befehl) können Sie nach Text suchen und Visual Studio-Befehle ausführen. Das Feld **Find/Command** (Suchen/Befehl) ist weiterhin als Steuerelement für die Symbolleiste verfügbar, wird standardmäßig aber nicht mehr angezeigt. Sie können das Feld **Find/Command** (Suchen/Befehl) einblenden, indem Sie in der Symbolleiste**Standard** auf **Schaltflächen hinzufügen oder entfernen** klicken und anschließend auf **Suchen** klicken.

 Leiten Sie einen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl mit einem Größer-als-Zeichen (>) ein, um ihn auszuführen.

 Das Feld **Suchen/Befehl** speichert die letzten 20 Eingaben und zeigt sie in einer Dropdownliste an. Mithilfe der Pfeiltasten kann in der Liste navigiert werden.

 ![Befehlsfeld "&#47;suchen](../ide/media/findcommandbox.png "Findcommandfeld") " Feld "Suchen/Befehl"

## <a name="searching-for-text"></a>Nach Text suchen
 Wenn Sie Text im Feld **Suchen/Befehl** angeben und dann die EINGABETASTE drücken, durchsucht Visual Studio standardmäßig das aktuelle Dokument oder Tool Fenster mithilfe der Optionen, die im Dialogfeld **in Dateien suchen** angegeben sind. Weitere Informationen finden Sie untersuchen [und Ersetzen von Text](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Eingeben von Befehlen
 Um über das Feld **Suchen/Befehl** einen einzelnen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl oder Alias auszugeben, anstatt nach Text zu suchen, geben Sie den gewünschten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Befehl mit einem vorangestellten Größer-als-Zeichen (>) ein. Beispiel:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

 Darüber hinaus können Sie auch das Befehlsfenster zum Eingeben und Ausführen von einzelnen oder mehreren Befehlen verwenden. Einige Befehle oder Aliase können eigenständig eingegeben und ausgeführt werden, für andere erfordert die Syntax die Angabe von Argumenten. Eine Liste der Befehle, die über Argumente verfügen, finden Sie unter [Visual Studio-Befehle](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Escapezeichen
 Ein Caretzeichen (^) in einer Befehlszeile bedeutet, dass das unmittelbar darauf folgende Zeichen literal und nicht als Steuerzeichen interpretiert wird. Dies ermöglicht das Einbetten von geraden Anführungszeichen ("), Leerzeichen, vorangestellten Schrägstrichen, Caretzeichen oder beliebigen anderen Literalzeichen in einen Parameter- oder Schalterwert, mit Ausnahme von Schalternamen. Beispiel:

```
>Edit.Find ^^t /regex
```

 Die Funktionsweise des Caretzeichens ist unabhängig davon, ob es in Anführungszeichen eingeschlossen ist oder nicht. Wenn ein Caretzeichen das letzte Zeichen in einer Zeile ist, wird es ignoriert.

## <a name="see-also"></a>Weitere Informationen
 [Befehlsfenster](../ide/reference/command-window.md) zum Suchen [und Ersetzen von Text](../ide/finding-and-replacing-text.md)
