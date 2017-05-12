---
title: "IActiveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScript-Schnittstelle"
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript
Stellt die Methoden bereit, die erforderlich sind, das Skriptmodul zu initialisieren.  Das Skriptmodul muss die `IActiveScript`\-Schnittstelle implementieren.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informiert das Skriptmodul über die [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Site, die vom Host bereitgestellt wird.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Ruft das Site\-Objekt ab, das dem Windows Script\-Modul zugeordnet ist.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Setzt das Skriptmodul in den angegebenen Zustand.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Ruft den aktuellen Zustand des Skriptmoduls ab.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Veranlasst das Skriptmodul, um jedes aktuell geladene Skript abzubrechen, seinen Zustand zu verlieren und alle Schnittstellenzeiger freizugeben, die es andere Objekte muss und so gibt einen geschlossenen Zustand.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Fügt den Namen eines Elements auf Stammebene den Namespace des Skriptmoduls hinzu.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Fügt eine Typbibliothek dem Namespace für das Skript hinzu.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Ruft die `IDispatch`\-Schnittstelle für das ausgeführte Skript ab.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Ruft einen Skripterstellung\-Modul\-definierten Bezeichner für den aktuell ausgeführten Thread ab.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Ruft einen Skripterstellung\-Modul\-definierten Bezeichner für den Thread ab, der mit dem angegebenen Thread Microsoft Win32\-Fensters zugeordnet ist.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Ruft den aktuellen Zustand eines Skriptthreads ab.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Unterteilt die Ausführung eines laufenden Skriptthreads.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Klont das aktuelle Skriptmodul \(abzüglich aller aktuellen Ausführungsstandes\) und gibt ein geladenes Skriptmodul zurück, das keine Website im aktuellen Thread hat.|  
  
## Siehe auch  
 [Windows Script\-Schnittstellenverweis](../../winscript/reference/windows-script-interfaces-reference.md)