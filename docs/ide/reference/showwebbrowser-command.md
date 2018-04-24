---
title: Befehl „ShowWebBrowser“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f699623d15a400b58b3b546a7eb93300385903a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="showwebbrowser-command"></a>Befehl "ShowWebBrowser"
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