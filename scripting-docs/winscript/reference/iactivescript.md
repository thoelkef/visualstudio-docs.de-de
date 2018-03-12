---
title: IActiveScript | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescript"></a>IActiveScript
Stellt die Methoden zum Initialisieren des verwendeten Skriptmoduls. Das Skriptmodul implementieren muss die `IActiveScript` Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informiert das Skriptmodul von der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Website, die vom Host bereitgestellt.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Ruft das Site-Objekt, das das Windows-Skriptmodul zugeordnet.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Setzt das Skriptmodul in den angegebenen Zustand übergeht.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Ruft den aktuellen Status des verwendeten Skriptmoduls ab.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Bewirkt, dass das Skriptmodul in verwerfen Sie alle derzeit geladenes Skript, verlieren den Zustand, und lassen Sie alle Schnittstellenzeiger er für andere Objekte, daher eingeben Zustand "geschlossen" aufweist.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Namespace für das Skriptmodul hinzugefügt den Namen eines Elements auf der Stammebene.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Der Namespace für das Skript wird eine Typbibliothek hinzugefügt.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Ruft die `IDispatch` Schnittstelle für die Ausführung des Skripts.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Ruft einen Bezeichner scripting-Engine-definiert, für den gerade ausgeführten Thread ab.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Ruft einen scripting-Engine-definierten Bezeichner für den Thread, der dem angegebenen Microsoft Win32-Thread zugeordnet.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Ruft den aktuellen Status eines Threads Skript ab.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Unterbricht die Ausführung von einem ausgeführten Skriptthread an.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Klont das aktuelle Skriptmodul (minus alle aktuellen Ausführungsstatus), Rückgabe einer geladenen Skriptmodul, die keine Standort in den aktuellen Thread verfügt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)