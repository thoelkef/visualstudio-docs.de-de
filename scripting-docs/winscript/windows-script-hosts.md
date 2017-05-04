---
title: "Windows Script Hosts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Script Host, Implementieren von Hosts"
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows Script Hosts
Wenn Sie Microsoft Windows\-Skripthost implementieren, können Sie sich davon ausgehen, dass ein Skriptmodul nur die [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)\-Schnittstelle im Kontext des Basisthreads aufruft, solange der Host das folgende Aktionen ausführt:  
  
-   Wählt einen niedrigen Thread aus \(im Allgemeinen den Thread, der die Meldungsschleife enthält\).  
  
-   Instanziiert das Skriptmodul im Basisthread.  
  
-   Aufrufsskriptmodulmethoden nur vom Basisanbieter Thread, wenn speziell zugelassen, wie in den Fällen von [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) und von [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
-   Ruft das Dispatchobjekt des Skriptmoduls nur vom Basisanbieter Thread auf.  
  
-   Stellt sicher, dass die Meldungsschleife in den Basisthread ausgeführt wird, wenn ein Fensterhandle bereitgestellt wird.  
  
-   Stellt sicher dass Objekte in den Ereignissen des Objektmodells des Hosts nur Quelle niedrigen Thread.  
  
 Diese Regeln werden automatisch von allen Singlethreadanwendung Hosts erfolgreich.  Das eingeschränkte Modell, das oben beschrieben wird, ist beabsichtigt genug lose beibehalten, einem Host ermöglichen, ein festes Skript, indem [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) von einem anderen Thread abbrechen \(initiiert durch einen STRG\+UNTBR\-Handler oder Ähnlichem\), oder aufruft, ein Skript in einem neuen Thread mithilfe [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) zu duplizieren.  
  
## Hinweise  
 Keine dieser Einschränkungen gelten für einen Host zu, der beschreibt, wie eine Freethreadmodell [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)\-Schnittstelle und ein Freethreadobjektmodell zu implementieren.  Ein solcher Host kann die [IActiveScript](../winscript/reference/iactivescript.md)\-Schnittstelle von jedem Thread, ohne Einschränkung verwenden.  
  
## Siehe auch  
 [\<PAVE OVER\> Microsoft Windows\-Skriptschnittstellen – Einführung](http://msdn.microsoft.com/library/3d10169f-2984-49ef-90c6-dd89c97f1dd6)