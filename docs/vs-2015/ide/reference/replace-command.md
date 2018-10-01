---
title: Befehl „Ersetzen“ | Microsoft-Dokumentation
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
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d4de79f804637f13b0fd487b1db62ad4bf7490ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513359"
---
# <a name="replace-command"></a>Befehl "Ersetzen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Befehl Ersetzen](https://docs.microsoft.com/visualstudio/ide/reference/replace-command).  
  
  
Ersetzt Text in Dateien mit einem Teil der Optionen, die auf der Registerkarte **In Dateien ersetzen** im Fenster **Suchen und Ersetzen** verfügbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
```  
  
## <a name="arguments"></a>Argumente  
 `findwhat`  
 Erforderlich. Der Text, für den eine Übereinstimmung ermittelt werden soll.  
  
 `replacewith`  
 Erforderlich. Der Text, durch den der übereinstimmende Text ersetzt werden soll  
  
## <a name="switches"></a>Schalter  
 /all oder /a  
 Dies ist optional. Ersetzt den Suchtext bei jedem Vorkommen durch den Ersetzungstext  
  
 /case oder /c  
 Dies ist optional. Übereinstimmungen treten nur auf, wenn die groß und klein geschriebenen Zeichen mit den im `findwhat`-Argument angegebenen übereinstimmen.  
  
 /doc oder/d  
 Dies ist optional. Sucht nur im aktuellen Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).  
  
 /hidden oder /h  
 Dies ist optional. Sucht nach ausgeblendetem und reduziertem Text, z.B. nach den Metadaten eines Designzeit-Steuerelements, einem ausgeblendeten Bereich in einem umrissenen Dokument oder einer reduzierten Klasse bzw. Methode  
  
 /open oder /o  
 Dies ist optional. Sucht in allen geöffneten Dokumenten, als wären sie ein einziges Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).  
  
 /options oder /t  
 Dies ist optional. Zeigt eine Liste der aktuellen Optionseinstellungen für die Suche an und führt keine Suche aus.  
  
 /proc oder /p  
 Dies ist optional. Sucht nur in der aktuellen Prozedur. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).  
  
 /regex oder /r  
 Dies ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, die Textmuster anstelle von Literalzeichen darstellen. Eine vollständige Liste von Zeichen für reguläre Ausdrücke finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /reset oder /e  
 Dies ist optional. Legt die Suchoptionen wieder auf die Standardeinstellungen fest und führt keine Suche aus.  
  
 /sel oder /s  
 Dies ist optional. Sucht nur in der aktuellen Auswahl. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).  
  
 /up oder /u  
 Dies ist optional. Sucht von der aktuellen Position in der Datei bis zum Anfang der Datei. Standardmäßig beginnt die Suche bei der aktuellen Position in der Datei und wird bis zum Ende der Datei ausgeführt.  
  
 /wild oder /l  
 Dies ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, um ein Zeichen oder eine Abfolge von Zeichen darzustellen.  
  
 /word oder /w  
 Dies ist optional. Sucht nur nach ganzen Wörtern.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird `btnSend` in allen geöffneten Dokumenten durch `btnSubmit` ersetzt.  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Suchen und Ersetzen von Text](../../ide/finding-and-replacing-text.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)



