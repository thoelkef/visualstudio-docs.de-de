---
title: Befehl „ShowWebBrowser“ | Microsoft-Dokumentation
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
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de730650216f67d3f620fa85cad0a98148ce2ee3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511939"
---
# <a name="showwebbrowser-command"></a>Befehl "ShowWebBrowser"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Befehl "ShowWebBrowser"](https://docs.microsoft.com/visualstudio/ide/reference/showwebbrowser-command).  
  
  
Zeigt die in einem Webbrowserfenster angegebene URL entweder in der integrierten Entwicklungsumgebung (IDE) oder außerhalb der IDE an.  
  
## <a name="syntax"></a>Syntax  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Argumente  
 `URL`  
 Erforderlich. URL (Uniform Resource Locator) für die Website  
  
## <a name="switches"></a>Schalter  
 /new  
 Dies ist optional. Gibt an, dass die Seite in einer neuen Instanz des Webbrowsers angezeigt wird  
  
 /ext  
 Dies ist optional. Gibt an, dass die Seite im Standard-Webbrowser außerhalb der IDE angezeigt wird  
  
## <a name="remarks"></a>Hinweise  
 Der Alias für den Befehl **ShowWebBrowser** ist **navigate** oder **nav**.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Homepage von MSDN Online in einem Webbrowser außerhalb der IDE gezeigt. Falls bereits eine Instanz des Webbrowsers geöffnet ist, wird sie verwendet. Andernfalls wird eine neue Instanz gestartet.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)



