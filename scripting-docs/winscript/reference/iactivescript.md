---
title: IActiveScript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b7e3a0172a798eab9a743f446dff3d339a785b2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150998"
---
# <a name="iactivescript"></a>IActiveScript
Stellt die Methoden, die zum Initialisieren der Skript-Engine. Muss die Skript-Engine implementiert die `IActiveScript` Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informiert die Skript-Engine, der die [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Website, die vom Host bereitgestellt wird.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Ruft das zugeordnete Windows-Skript-Engine-Objekt ab.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Platziert die Skript-Engine in den angegebenen Zustand.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Ruft den aktuellen Status des verwendeten Skriptmoduls ab.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Bewirkt, dass die Skript-Engine alle aktuell geladenen Skripts abbrechen, verlieren den Zustand und release-Schnittstellenzeiger auf die sie für andere Objekte, also einen geschlossenen Zustand verfügt.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Der Name eines Elements auf der Stammebene wird auf die Skript-Engine-Namespace hinzugefügt.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Der Namespace für das Skript wird eine Typbibliothek hinzugefügt.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Ruft die `IDispatch` Schnittstelle für das ausgeführte Skript ein.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Ruft eine scripting-Engine-definierten Bezeichner für den aktuell ausgeführten Thread ab.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Ruft ab eine scripting-Engine-definierten Bezeichner für den Thread, der dem angegebenen Microsoft Win32-Thread zugeordnet.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Ruft den aktuellen Status eines Threads Skript ab.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Unterbricht die Ausführung einen ausgeführten Skriptthread an.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Klont die aktuelle Skript-Engine (minus alle aktuellen Ausführungsstatus), eine geladene Skript-Engine, die keine Standort in den aktuellen Thread zurückgibt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)