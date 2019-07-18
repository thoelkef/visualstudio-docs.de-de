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
ms.openlocfilehash: e0a4a8482dc1c2c66a45902f2f3382b179b46b13
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199120"
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
 Optional. Gibt die Anzahl der anzuzeigenden Zeilen an.  
  
 /Current  
 Dies ist optional. Zeigt die aktuelle Zeile an.  
  
 /File:`filename`  
 Optional. Pfad der anzuzeigenden Datei. Ist kein Dateiname angegeben, zeigt der Befehl den Quellcode für die Zeile der aktuellen Anweisung an.  
  
 /Line:`number`  
 Optional. Zeigt eine bestimmte Zeilennummer an.  
  
 /ShowLineNumbers:`yes|no`  
 Optional. Gibt an, ob Zeilennummern angezeigt werden sollen.  
  
## <a name="remarks"></a>Anmerkungen  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel listet den Quellcode aus Zeile 4 der Datei „Form1.vb“ mit eingeblendeten Zeilennummern an.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)
