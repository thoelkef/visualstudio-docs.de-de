---
title: Neues im Debugger in Visual Studio 2015 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 743875ef4ab7582bd4c1a254c82f168b96ba8208
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188616"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Neues im Debugger in Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Informationen zu allen Neuerungen hinsichtlich Debugging und Diagnose in Visual Studio 2015 Update 1 finden Sie in den [Anmerkungen zur Version Visual Studio 2015 Update 1](https://www.visualstudio.com/news/vs2015-update1-vs#debug).  
  
 Informationen zu allen Neuerungen hinsichtlich Debugging und Diagnose in Visual Studio 2015 RTM finden Sie in den [Anmerkungen zur Version Visual Studio 2015](https://www.visualstudio.com/news/vs2015-vs#debug).  
  
## <a name="visual-studio-2015-update-1-changes"></a>Visual Studio 2015 Update 1 – Änderungen  
 „Bearbeiten und Fortfahren“ von C++ unterstützt weitere Features. Weitere Informationen finden Sie unter [bearbeiten und Fortfahren (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
 Zum Debuggen von Visual C++-Zugriffsverletzungen gibt ein neues Dialogfeld für Ausnahmen den Zeiger an, der die Ausnahme ausgelöst hat. Weitere Informationen finden Sie unter [How Can I Debug an Access Violation?](../debugger/how-can-i-debug-an-access-violation-q.md) und [Verbesserung beim Debuggen von C++-Zugriffsverletzungen in Visual Studio 2015 Update 1](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)  
  
## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Visual Studio 2015 RTM – Debugger-Benutzeroberfläche und Hotkey-Änderungen  
 An der Benutzeroberfläche der Ausnahme- und Haltepunkteinstellungen wurden erhebliche Änderungen vorgenommen.  
  
### <a name="breakpoints"></a>Haltepunkte  
 In Visual Studio 2015 wurde eine neue Methode zum Konfigurieren von Haltepunkten eingeführt: das Fenster **Haltepunkteinstellungen** .  
  
 Im Folgenden eine Zusammenfassung der wichtigsten Fenster und Hotkeys:  
  
|Feature|Menü|Hotkey|  
|-------------|-------------------|------------|  
|Neuer Haltepunkt, Haltepunkt ein/aus|**Debuggen / Haltepunkt umschalten**<br /><br /> Kontextmenü im Editor / **Haltepunkt einfügen**<br /><br /> Am linken Rand klicken|F9|  
|Neuer Funktionshaltepunkt|**Debuggen / Neuer Haltepunkt / Funktionshaltepunkt**|Verwenden Sie in Visual Studio 2015 RTM (mit keine Updates) ALT + F9, B<br /><br /> Verwenden Sie in Visual Studio 2015 Update 1 und höher, STRG + B|  
|Fenster**Haltepunkte** |**Debuggen / Windows / Haltepunkte**|STRG + ALT + B|  
|**Haltepunkteinstellungen**, **Bedingungen**|Kontextmenü für den Haltepunkt / **Bedingungen**|ALT + F9, C|  
|**Haltepunkteinstellungen**, **Aktionen**|Kontextmenü für den Haltepunkt / **Aktionen**|Kein Hotkey|  
  
 Weitere Informationen finden Sie in den folgenden Artikeln:  
  
1.  [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)  
  
2.  [Neue Haltepunktkonfiguration, Darstellung](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)  
  
3.  [Haltepunktkonfiguration, Darstellung](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)  
  
### <a name="exception-settings"></a>Ausnahmeeinstellungen  
 Mithilfe des neuen Fensters **Ausnahmeeinstellungen** können Sie die Art der Ausnahmebehandlung für einzelne Ausnahmen oder Kategorien von Ausnahmen angeben.  
  
|Feature|Menü|Hotkey|  
|-------------|-------------------|------------|  
|Fenster**Ausnahmeeinstellungen** |**Debuggen / Windows / Ausnahmeeinstellungen**|STRG + ALT + E|  
  
 Weitere Informationen finden Sie in den folgenden Artikeln:  
  
1.  [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)  
  
2.  [Das neue Fenster "Ausnahmen"](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)  
  
### <a name="edit-and-continue"></a>Bearbeiten und Fortfahren  
 In Visual Studio 2015 können Sie die Einstellungen zum Bearbeiten und Fortfahren auf der Seite **Extras / Optionen / Debugging / Allgemein** festlegen. In früheren Versionen befanden sich diese Einstellungen in einer separaten Kategorie mit Optionen.  
  
### <a name="attach-to-process"></a>An den Prozess anhängen  
 In Visual Studio 2015 ist der Befehl „An den Prozess anhängen“ nur aus dem Menü „Debuggen“ verfügbar. In früheren Versionen war er auch aus dem Menü „Extras“ verfügbar. Der Hotkey STRG + ALT + P funktioniert in allen Versionen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)



