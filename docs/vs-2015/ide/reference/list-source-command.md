---
title: Befehl „Quelle auflisten“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ae2ed3e8a9c07d59f5b1c2fe2350956a54dfaa66
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54761506"
---
# <a name="list-source-command"></a>Befehl "Quelle auflisten"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Zeigt die angegebenen Quellcodezeilen an.  
  
## <a name="syntax"></a>Syntax  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>Schalter  
 /Count:`number`  
 Dies ist optional. Gibt die Anzahl der anzuzeigenden Zeilen an.  
  
 /Current  
 Dies ist optional. Zeigt die aktuelle Zeile an.  
  
 /File:`filename`  
 Dies ist optional. Pfad der anzuzeigenden Datei. Ist kein Dateiname angegeben, zeigt der Befehl den Quellcode für die Zeile der aktuellen Anweisung an.  
  
 /Line:`number`  
 Dies ist optional. Zeigt eine bestimmte Zeilennummer an.  
  
 /ShowLineNumbers:`yes|no`  
 Dies ist optional. Gibt an, ob Zeilennummern angezeigt werden sollen.  
  
## <a name="remarks"></a>Anmerkungen  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel listet den Quellcode aus Zeile 4 der Datei „Form1.vb“ mit eingeblendeten Zeilennummern an.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)
